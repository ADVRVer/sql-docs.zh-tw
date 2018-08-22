---
title: 資料管理檢視 (Dmv) （適用於 SQL Server 機器學習服務 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8d7d20d396ca5b853d959c84a371fe808415c5fb
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394006"
---
# <a name="dmvs-for-sql-server-machine-learning-services"></a>SQL Server Machine Learning 服務的 Dmv
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

該文會列出系統目錄檢視和 SQL Server 中的機器學習服務相關的 Dmv。

擴充事件的相關資訊，請參閱[擴充事件適用於 machine learning](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)。

> [!TIP]
> 使用內建報表來監視機器學習服務工作階段和封裝使用情形。 如需詳細資訊，請參閱 <<c0> [ 監視使用 Management Studio 中的自訂報表的機器學習服務](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)。

## <a name="system-configuration-and-system-resources"></a>系統組態和系統資源

您可以監視和分析使用外部指令碼所使用的資源[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]系統目錄檢視和 Dmv。

+ [ sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)

  傳回使用者連線和系統工作階段的資訊。 您可以查看 *session_id* 資料行來識別系統工作階段；大於或等於 51 的值是使用者連線，小於 51 的值則是系統處理序。

+ [sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)

  針對伺服器所使用的每個系統效能計數器，各傳回一個資料列。  您可以利用這項資訊來查看執行了多少指令碼、使用了哪些驗證模式來執行哪些指令碼，或是在執行個體上總共發出了多少 R 呼叫。

  此範例只會取得與 R 指令碼相關的計數器：

  ```SQL
  SELECT * from sys.dm_os_performance_counters WHERE object_name LIKE '%External Scripts%'
  ```

  此 DMV 會針對每一執行個體的外部指令碼回報下列計數器：

  + **總執行次數**： 本機或遠端呼叫所啟動的外部處理序的數目
  + **平行執行次數**： 包含指令碼次數_@parallel_規格且[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]能夠產生及使用平行查詢計畫
  + **資料流執行次數**： 資料流的功能已叫用次數
  + **SQL CC 執行**： 數字的外部指令碼的執行位置呼叫具現化遠端及 SQL Server 作為計算內容
  + **Implied Auth.登入次數**：使用隱含驗證來發出 ODBC 回送呼叫的次數；亦即 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 代表傳送指令碼要求的使用者執行呼叫
  + **總執行時間 （毫秒）**： 呼叫與完成呼叫之間所經過的時間
  + **執行錯誤次數**：指令碼回報錯誤的次數。 此計數不包含 R 錯誤。


+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)

  此 DMV 會針對目前正在執行外部指令碼的每個背景工作帳戶回報一個資料列。 請注意，此背景工作帳戶與傳送指令碼之人員的認證不同。 如果單一 Windows 使用者傳送多個指令碼要求，則系統只會指派一個背景工作帳戶來處理來自該使用者的所有要求。 如果有不同的 Windows 使用者登入以執行外部指令碼，該要求將會由個別的背景工作帳戶處理。

  如果目前並未執行任何指令碼，此 DMV 就不會傳回任何結果；因此，最適用於監視長時間執行的指令碼。 它會傳回下列值：

  + **external_script_request_id**: GUID，它也會做為暫時的名稱，用來儲存指令碼和中繼結果的工作目錄
  + **語言**： 值，例如`R`所代表的外部指令碼語言
  + **degree_of_parallelism**： 一個整數，表示平行數目的程序，使用
  + **external_user_name**: Launchpad 背景工作帳戶，例如**SQLRUser01**

+ [sys.dm_external_script_execution_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)

  此 DMV 被提供進行內部監視 （遙測） 來追蹤多少外部指令碼呼叫的執行個體上。 遙測服務啟動時[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]執行並每次呼叫特定的機器學習服務函數時遞增以磁碟為基礎的計數器。

  此計數器會遞增每個特定的追蹤函式呼叫。 例如，如果呼叫 `rxLinMod` 並以平行方式執行，此計數器會遞增 1。
  
  一般而言，只要產生效能計數器的處理序正在使用，效能計數器就會有效。 因此，DMV 上的查詢無法顯示已停止執行之服務的詳細資料。 例如，如果 Launchpad 建立多個平行 R 作業，但 Windows 作業物件很快地執行它們後又將它們清除，DMV 可能就不會顯示任何資料。
 
  不過，此 DMV 所追蹤的計數器會繼續執行，而 dm_external_script _execution 計數器的狀態則會透過使用對磁碟的寫入來保存，即使執行個體已關閉。
 
 如需有關 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 所使用之系統效能計數器的詳細資訊，請參閱[使用 SQL Server 物件](../../relational-databases/performance-monitor/use-sql-server-objects.md)。

## <a name="resource-governor-views"></a>Resource Governor 檢視

在支援資源管理員的版本中，建立適用於 R 或 Python 工作負載的外部資源集區可以是 en 有效的方法，來追蹤和管理資源。

+ [sys.resource_governor_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)

  傳回目前資源集區狀態的相關資訊、資源集區的目前組態和資源集區統計資料。

  > [!IMPORTANT]
  > 
  > 您必須先修改適用於其他伺服器服務的資源集區，才能將額外的資源配置給 R Services。

+ [sys.resource_governor_external_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)

  一個新的目錄檢視，其中顯示外部資源集區的目前設定值。
  在 Enterprise Edition 中，您可以設定額外的外部資源集區：例如，您可能會決定將在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 中執行之 R 作業的資源與來自遠端用戶端之作業的資源分開處理。

  > [!NOTE]
  > 
  > 在 Standard Edition 中，所有的外部指令碼工作會執行相同的外部預設資源集區中。

+ [sys.resource_governor_workload_groups](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)

  傳回工作負載群組統計資料，以及工作負載群組目前的設定。 這個檢視可以與 `sys.dm_resource_governor_resource_pools` 聯結以取得資源集區名稱。
  針對外部指令碼，已新增一個新的資料行，其中顯示與工作負載群組關聯之外部集區的識別碼。

+ [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)

  一個新的系統目錄檢視，可讓您查看與特定資源集區產生親和性的處理器和資源。

  針對 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 中的每個排程器，各傳回一個資料列，其中每個排程器都會對應至個別的處理器。 請利用這份檢視來監視排程器的狀況或識別失控的工作。

  在預設設定下，系統會自動將工作負載集區指派給處理器，因此沒有任何親和性值可供傳回。

  親和性排程會將資源集區對應至由指定識別碼識別的 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 排程。 這些識別碼會對應中的值`scheduler_id`中的資料行`sys.dm_os_schedulers`。


> [!NOTE] 
> 
> 雖然只有在 Enterprise 和 Developer 版本中才能設定和自訂資源集區，但在所有版本中都有提供預設集區及 DMV。 因此，您可以在 Standard Edition 中使用這些 Dmv 來判斷您的外部指令碼工作的資源上限。

如需有關監視 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 執行個體的一般資訊，請參閱[目錄檢視](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)和 [Resource Governor 相關的動態管理檢視](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)。

## <a name="monitoring-script-execution"></a>監視指令碼執行

在中執行的 R 和 Python 指令碼[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]啟動[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]介面。 不過，Launchpad 的資源並未受到管理或個別監視，因為它被認定為是由 Microsoft 所提供、以適當方式管理資源的安全服務。

使用管理在 Launchpad 服務下執行的個別指令碼[Windows 作業物件](/windows/desktop/ProcThread/job-objects)。 作業物件可讓您將處理序群組當作一個單位來管理。 每個作業物件都是階層式物件，並控制與其關聯之所有處理序的屬性。 在作業物件上執行的作業會影響與該作業物件關聯的所有處理序。

因此，如果您需要終止一個與某個物件關聯的作業，請注意，所有相關的處理序也將一併終止。 如果您正在執行指派給 Windows 作業物件的 R 指令碼，而該指令碼執行必須終止的相關 ODBC 作業，則父系 R 指令碼處理序也將一併終止。

如果您開始使用平行處理外部指令碼時，單一的 Windows 工作物件會管理所有平行子處理程序。

若要判斷處理序是否是在作業中執行，請使用 `IsProcessInJob` 函數。

## <a name="next-steps"></a>後續步驟

[管理及監視機器學習服務方案](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
