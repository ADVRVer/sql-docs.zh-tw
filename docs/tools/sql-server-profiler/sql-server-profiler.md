---
title: "SQL Server Profiler |Microsoft 文件"
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- traces [SQL Server], SQL Server Profiler
- database monitoring [SQL Server], SQL Server Profiler
- tuning databases [SQL Server], SQL Server Profiler
- SQL Server Profiler
- server performance [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler]
- tracing [SQL Server]
- monitoring performance [SQL Server], SQL Server Profiler
- events [SQL Server], SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
- tools [SQL Server], SQL Server Profiler
- database performance [SQL Server], SQL Server Profiler
- trace [SQL Server]
ms.assetid: 3ad5f33d-559e-41a4-bde6-bb98792f7f1a
caps.latest.revision: 46
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 55fa14d4d8e28f602c49613cf81e981c12856177
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-profiler"></a>SQL Server Profiler
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]是建立及管理追蹤和分析和重新執行追蹤結果的介面。 事件會儲存於追蹤檔案中，稍後在嘗試診斷問題時，可以用來進行分析或是重新執行特定的一連串步驟。  
  
>**重要！！**  
> 我們宣佈適用於 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤擷取和追蹤重新執行的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 已被取代。 SQL Server 2016 **可以使用** 這些功能，但是之後的版本會移除這些功能。
>   
>  包含 Microsoft SQL Server 追蹤和重新執行物件的 *Microsoft.SqlServer.Management.Trace* 命名空間也將被取代。                     
**請注意** ，適用於 Analysis Services 工作負載的 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 「未」遭取代，而且將會繼續受支援。
>
> 請在我們的 **[[連接] 頁面](https://connect.microsoft.com/SQLServer/Feedback)**

 ## <a name="where-is-the-profiler"></a>Profiler 位於何處？
 
 您可以從 SSMS 內以數種方式啟動 Profiler。 [以下是列出啟動分析工具的方式的主題。](https://msdn.microsoft.com/library/ms173799.aspx)
  
## <a name="capture-and-replay-trace-data"></a>擷取並重新執行追蹤資料 
下表顯示我們建議在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中用來擷取和重新執行追蹤資料的功能。
  
||||  
|-|-|-|  
|**功能 \ 目標工作負載**|**關聯式引擎**|**Analysis Services (英文)**|  
|**追蹤擷取**|SQL Server Management Studio 中的[擴充事件](https://msdn.microsoft.com/library/bb630282.aspx) 圖形化使用者介面|SQL Server Profiler|  
|**重新執行追蹤**|[Distributed 的 Replay](https://msdn.microsoft.com/library/ff878183.aspx)|SQL Server Profiler|  
  
## <a name="sql-server-profiler"></a>SQL Server Profiler  
 Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 是「SQL 追蹤」的圖形化使用者介面，可用來監視 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 或 Analysis Services 的執行個體。 您可以擷取每一個事件的相關資料，並將資料儲存至檔案或資料表，以供稍後分析。 例如，您可以監視生產環境，查看哪些預存程序由於執行速度過慢而影響效能。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]用於活動例如：  
  
-   逐步執行問題查詢來找出問題原因。  
  
-   尋找和診斷執行速度很慢的查詢。  
  
-   擷取造成問題的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式系列。 之後，就可以利用已儲存的追蹤，在能夠診斷問題的伺服器上複製這個問題。  
  
-   監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的效能來微調工作負載。 如需有關針對資料庫工作負載來微調實體資料庫設計的資訊，請參閱＜ [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)＞。  
  
-   將效能計數器相互關聯以診斷問題。  
  
 另外，[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 也支援稽核在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上執行的動作。 稽核會將安全性相關動作記錄下來，供安全性管理員稍後進行檢閱。  
  
## <a name="sql-server-profiler-concepts"></a>SQL Server Profiler 概念  
 若要使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，您必須對於描述工具功能的專門用語有所了解。  
  
>**注意！** 使用 SQL Server Profiler 時，了解 SQL 追蹤真的很有幫助。 如需詳細資訊，請參閱 [SQL Trace](../../relational-databases/sql-trace/sql-trace.md)。  
  
 **事件**  
 事件是在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]之執行個體中產生的動作。 範例如下：  
  
-   登入連接、失敗及中斷連接。  
  
-   Transact-SQL SELECT、INSERT、UPDATE 及 DELETE 陳述式。  
  
-   遠端程序呼叫 (RPC) 批次狀態。  
  
-   預存程序的啟動或結束。  
  
-   預存程序內部陳述式的啟動或結束。  
  
-   SQL 批次的啟動或結束。  
  
-   寫入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔的錯誤。  
  
-   資料庫物件上的鎖定被取得或釋放。  
  
-   開放式資料指標。  
  
-   安全性權限檢查。  
  
 事件產生的所有資料，都會在追蹤中以單一資料列呈現。 另有資料行與此資料列交叉，用以詳細描述該事件。  
  
 **EventClass**  
 事件類別是一種可追蹤的事件類型。 事件類別包含所有可由事件來報告的資料。 事件類別的範例如下：  
  
-   **SQL:BatchCompleted**  
  
-   **稽核登入**  
  
-   **稽核登出**  
  
-   **Lock： 取得**  
  
-   **Lock： 發行**  
  
 **EventCategory**  
 事件類別目錄用來定義事件在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中的分組方式。 例如，所有的鎖定事件類別都會在 **Locks** 事件類別目錄中予以分組。 然而，事件類別目錄僅存在於 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中。 這個詞彙無法反映 Engine 事件的分組方式。  
  
 **DataColumn**  
 資料行是追蹤中所擷取之事件類別的屬性。 因為事件類別會決定可收集的資料類型，所以並不是所有的資料行都適用於所有的事件類別。 例如，在擷取 **Lock:Acquired** 事件類別的追蹤中， **BinaryData** 資料行包含鎖定分頁識別碼或資料列的值，但是 **Integer Data** 資料行則不包含任何值，因為它不適用於所擷取的事件類別。  
  
 **範本**  
 範本可定義追蹤的預設組態。 它特別包含您要用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來監視的事件類別。 例如，您可以建立範本，其中指定要使用的事件、資料行及篩選。 範本不能被執行，但會儲存成 .tdf 副檔名的檔案。 一旦儲存之後，當您啟動以範本為依據的追蹤時，範本就會控制所要擷取的追蹤資料。  
  
 **追蹤**  
 追蹤會根據所選取的事件類別、資料行及篩選，來擷取資料。 例如，您可以建立追蹤來監視異常錯誤。 若要執行此作業，請選取 **Exception** 事件類別及 **Error**、 **State**和 **Severity** 資料行。 必須同時收集這三個資料行的資料，追蹤結果才能提供有意義的資料。 接著，您可以執行以此方式設定的追蹤，並收集出現在伺服器中之任何 **Exception** 事件的資料。 追蹤資料可以儲存起來，也可以立即用於分析。 稍後可以再重新執行追蹤，但有些事件 (例如 **Exception** 事件) 永遠也無法重新執行。 您也可以將追蹤儲存成範本，以在未來建立類似的追蹤。  
  
 SQL Server 提供兩種方式來追蹤 SQL Server 的執行個體：您可以透過 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤，或是使用系統預存程序追蹤。  
  
 **篩選器**  
 建立追蹤或範本時，您可以定義條件來篩選由事件所收集的資料。 若不想讓追蹤變得太大，您可加以篩選，只收集某些事件資料的子集。 例如，您可以在追蹤中將 Microsoft Windows 使用者名稱限制在特定的使用者，進而減少輸出資料。  
  
 如果沒有設定篩選條件，選定事件類別的所有事件都會傳回到追蹤輸出。  
  
## <a name="sql-server-profiler-tasks"></a>SQL Server Profiler 工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|列出 SQL Server 提供用於監視事件特定類型的預先定義範本，以及用以重新執行追蹤的必要權限。|[SQL Server Profiler 範本和權限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)|  
|描述如何執行 SQL Server Profiler。|[執行 SQL Server Profiler 所需的權限](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)|  
|描述如何建立追蹤。|[建立追蹤 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)|  
|描述如何指定追蹤檔案的事件和資料行。|[指定追蹤檔案的事件及資料行 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)|  
|描述如何將追蹤結果儲存至檔案。|[將追蹤結果儲存至檔案 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)|  
|描述如何將追蹤結果儲存至資料表。|[將追蹤結果儲存到資料表 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)|  
|描述如何篩選追蹤中的事件。|[篩選追蹤中的事件 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)|  
|描述如何檢視篩選資訊。|[檢視篩選資訊 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)|  
|描述如何修改篩選。|[修改篩選 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)|  
|描述如何設定追蹤檔案的檔案大小上限 (SQL Server Profiler)。|[設定追蹤檔案的檔案大小上限 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)|  
|描述如何設定追蹤資料表的資料表大小上限。|[設定追蹤資料表的資料表大小上限 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)|  
|描述如何啟動追蹤。|[啟動追蹤](../../tools/sql-server-profiler/start-a-trace.md)|  
|描述如何在連接至伺服器後自動啟動追蹤。|[在連接伺服器之後自動啟動追蹤 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)|  
|描述如何根據事件開始時間篩選事件。|[根據事件開始時間篩選事件 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-start-time-sql-server-profiler.md)|  
|描述如何根據事件結束時間篩選事件。|[根據事件結束時間篩選事件 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)|  
|描述如何篩選追蹤中的伺服器處理序識別碼 (SPID)。|[篩選追蹤中的伺服器處理序識別碼 &#40;SPIDs&#41; &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)|  
|描述如何暫停追蹤。|[暫停追蹤 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)|  
|描述如何停止追蹤。|[停止追蹤 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)|  
|描述如何在追蹤已暫停或停止之後執行追蹤。|[在追蹤暫停或停止之後執行追蹤 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)|  
|描述如何清除追蹤視窗。|[清除追蹤視窗 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)|  
|描述如何關閉追蹤視窗。|[關閉追蹤視窗 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/close-a-trace-window-sql-server-profiler.md)|  
|描述如何設定追蹤定義預設值。|[設定追蹤定義預設值 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)|  
|描述如何設定追蹤顯示預設值。|[設定追蹤顯示預設值 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)|  
|描述如何開啟追蹤檔案。|[開啟追蹤檔案 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)|  
|描述如何開啟追蹤資料表。|[開啟追蹤資料表 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)|  
|描述如何重新執行追蹤資料表。|[重新執行追蹤資料表 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)|  
|描述如何重新執行追蹤檔案。|[重新執行追蹤檔案 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)|  
|描述如何一次重新執行單一事件。|[一次重新執行一個事件 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-single-event-at-a-time-sql-server-profiler.md)|  
|描述如何重新執行至中斷點。|[重新執行至中斷點 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)|  
|描述如何重新執行至資料指標。|[重新執行至資料指標處 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)|  
|描述如何重新執行 Transact-SQL 指令碼。|[重新執行 Transact-SQL 指令碼 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-transact-sql-script-sql-server-profiler.md)|  
|描述如何建立追蹤範本。|[建立追蹤範本 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)|  
|描述如何修改追蹤範本。|[修改追蹤範本 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/modify-a-trace-template-sql-server-profiler.md)|  
|描述如何設定全域追蹤選項。|[設定全域追蹤選項 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)|  
|描述如何在追蹤時尋找值或資料行。|[在追蹤時尋找值或資料行 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)|  
|描述如何從執行中追蹤衍生範本。|[從執行中的追蹤衍生範本 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)|  
|描述如何從追蹤檔案或追蹤資料表衍生範本。|[從追蹤檔案或追蹤資料表衍生範本 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)|  
|描述如何建立用於執行追蹤的 Transact-SQL 指令碼。|[建立 Transact-SQL 指令碼以執行追蹤 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)|  
|描述如何匯出追蹤範本。|[匯出追蹤範本 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)|  
|描述如何匯入追蹤範本。|[匯入追蹤範本 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)|  
|描述如何從追蹤擷取指令碼。|[從追蹤中擷取指令碼 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/extract-a-script-from-a-trace-sql-server-profiler.md)|  
|描述如何使追蹤與 Windows 效能記錄資料相互關聯。|[使追蹤與 Windows 效能記錄資料相互關聯 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)|  
|描述如何組織追蹤中所顯示的資料行。|[組織追蹤內顯示的資料行 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)|  
|描述如何啟動 SQL Server Profiler。|[啟動 SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)|  
|描述如何儲存追蹤及追蹤範本。|[儲存追蹤及追蹤範本](../../tools/sql-server-profiler/save-traces-and-trace-templates.md)|  
|描述如何修改追蹤範本。|[修改追蹤範本](../../tools/sql-server-profiler/modify-trace-templates.md)|  
|描述如何使追蹤與 Windows 效能記錄資料相互關聯。|[使追蹤與 Windows 效能記錄資料相互關聯](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)|  
|描述如何使用 SQL Server Profiler 檢視及分析追蹤。|[使用 SQL Server Profiler 檢視和分析追蹤](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)|  
|描述如何使用 SQL Server Profiler 分析死結。|[使用 SQL Server Profiler 分析死結](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)|  
|描述如何在 SQL Server Profiler 中分析具有 SHOWPLAN 結果的查詢。|[在 SQL Server Profiler 中使用 SHOWPLAN 結果分析查詢](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)|  
|描述如何使用 SQL Server Profiler 篩選追蹤。|[使用 SQL Server Profiler 篩選追蹤](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md)|  
|描述如何使用 SQL Server Profiler 的重新執行功能。|[重新執行追蹤](../../tools/sql-server-profiler/replay-traces.md)|  
|列出 SQL Server Profiler 的即時線上說明主題。|[SQL Server Profiler F1 說明](../../tools/sql-server-profiler/sql-server-profiler-f1-help.md)|  
|列出 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 用以監視效能及活動的系統預存程序。|[SQL Server Profiler 預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)|  
  
## <a name="see-also"></a>另請參閱  
 [Locks 事件類別目錄](../../relational-databases/event-classes/locks-event-category.md)   
 [Sessions 事件類別目錄](../../relational-databases/event-classes/sessions-event-category.md)   
 [Stored 的 Procedures 事件類別目錄](../../relational-databases/event-classes/stored-procedures-event-category.md)   
 [TSQL 事件類別目錄](../../relational-databases/event-classes/tsql-event-category.md)   
 [伺服器效能與活動監視](../../relational-databases/performance/server-performance-and-activity-monitoring.md)  
  
  

