---
title: SERVERPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SERVERPROPERTY_TSQL
- SERVERPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SERVERPROPERTY function
- server instance property information [SQL Server]
- IsHadrEnabled server property
- instances of SQL Server, property information
- server properties [SQL Server]
ms.assetid: 11e166fa-3dd2-42d8-ac4b-04f18c612c4a
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 18aad5811c34eadfda4a2a7fabfdd7a9997311b5
ms.sourcegitcommit: 02b7fa5fa5029068004c0f7cb1abe311855c2254
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74127384"
---
# <a name="serverproperty-transact-sql"></a>SERVERPROPERTY (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

傳回有關伺服器執行個體的屬性資訊。  

![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
SERVERPROPERTY ( 'propertyname' )  
```  

> [!IMPORTANT]
> SQL Server 和 Azure SQL Database 的資料庫引擎版本號碼無法彼此相互比較，且更像是這些個別產品的內部組建編號。 Azure SQL Database 資料庫引擎是以和 SQL Server 資料庫引擎相同的程式碼基底作為基礎。 最重要的是，Azure SQL Database 資料庫引擎一律具有最新的 SQL 資料庫引擎位元。 Azure SQL Database 版本 12 比 SQL Server 版本 15 更新。

## <a name="arguments"></a>引數  

*propertyname*  
這是包含要傳回伺服器之屬性資訊的運算式。 *propertyname* 可以是下列值之一。  
  
|屬性|傳回的值|  
|--------------|---------------------|  
|BuildClrVersion|建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時所用的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 通用語言執行平台 (CLR) 版本。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|定序|伺服器預設定序的名稱。<br /><br /> NULL = 輸入無效，或發生錯誤。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|CollationID|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定序的識別碼。<br /><br /> 基底資料類型：**int**|  
|ComparisonStyle|Windows 的定序比較樣式。<br /><br /> 基底資料類型：**int**|  
|ComputerNamePhysicalNetBIOS|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體目前執行所在之本機電腦的 NetBIOS 名稱。<br /><br /> 如果是容錯移轉叢集中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 叢集執行個體，當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體容錯移轉到容錯移轉叢集中的其他節點時，這個值會跟著改變。<br /><br /> 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的獨立執行個體中，這個值會維持不變，且會傳回與 MachineName 屬性相同的值。<br /><br /> **注意：** 如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體在容錯移轉叢集中，且您想要取得容錯移轉叢集執行個體的名稱，請使用 MachineName 屬性。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|版本|已安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體產品版本。 使用這個屬性值決定功能和限制，例如[根據 SQL Server 版本計算容量限制](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)。 64 位元版的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會將 (64 位元) 附加至版本中。<br /><br /> 傳回：<br /><br /> 'Enterprise Edition'<br /><br /> 「Enterprise 版:核心授權」<br /><br /> 'Enterprise Evaluation Edition'<br /><br /> 'Business Intelligence Edition'<br /><br /> 'Developer Edition'<br /><br /> 'Express Edition'<br /><br /> 'Express Edition with Advanced Services'<br /><br /> 'Standard Edition'<br /><br /> 'Web Edition'<br /><br /> 'SQL Azure' 表示 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 或 [!INCLUDE[ssDW](../../includes/ssdw-md.md)]<br /><br /> 基底資料型別：**nvarchar(128)**|  
|EditionID|EditionID 表示安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體產品版本。 使用這個屬性值決定功能和限制，例如[根據 SQL Server 版本計算容量限制](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)。<br /><br /> 1804890536 = Enterprise<br /><br /> 1872460670 = Enterprise Edition：核心授權<br /><br /> 610778273= Enterprise Evaluation<br /><br /> 284895786 = Business Intelligence<br /><br /> -2117995310 = Developer<br /><br /> -1592396055 = Express<br /><br /> -133711905 = Express with Advanced Services<br /><br /> -1534726760 = Standard<br /><br /> 1293598313 = Web<br /><br /> 1674378470 = SQL 資料庫或 SQL 資料倉儲<br /><br /> 基底資料型別：**bigint**|  
|EngineEdition|安裝在伺服器上之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。<br /><br /> 1 = Personal 或 Desktop Engine (不適用於 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本中)。<br /><br /> 2 = Standard (Standard、Web 和 Business Intelligence 都會傳回這個值)。<br /><br /> 3 = Enterprise (Evaluation、Developer 和 Enterprise 版本都會傳回這個項目。)<br /><br /> 4 = Express (Express、Express with Tools 和 Express with Advanced Services 都會傳回這個項目)<br /><br /> 5 = [!INCLUDE[ssSDS](../../includes/sssds-md.md)]<br /><br /> 6 = [!INCLUDE[ssDW](../../includes/ssdw-md.md)]<br /><br /> 8 = 受控執行個體<br /><br /> 基底資料類型：**int**|  
|HadrManagerStatus|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更新版本。<br /><br /> 指出 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 管理員是否已經啟動。<br /><br /> 0 = 未啟動，暫止通訊。<br /><br /> 1 = 已啟動且在執行中。<br /><br /> 2 = 未啟動且失敗。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。|  
|InstanceDefaultDataPath|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至目前版本 (從 2015 晚期開始的更新)。<br /><br /> 執行個體資料檔案的預設路徑名稱。|  
|InstanceDefaultLogPath|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至目前版本 (從 2015 晚期開始的更新)。<br /><br /> 執行個體記錄檔的預設路徑名稱。|  
|InstanceName|使用者所連接之執行個體的名稱。<br /><br /> 如果執行個體名稱是預設執行個體、輸入無效，或發生錯誤，便傳回 NULL。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|IsAdvancedAnalyticsInstalled|若在設定時已安裝 [進階分析] 功能，則會傳回 1；否則會傳回 0。|  
|IsClustered|伺服器執行個體設定在容錯移轉叢集中。<br /><br /> 1 = 叢集。<br /><br /> 0 = 非叢集。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料類型：**int**|  
|IsFullTextInstalled|全文檢索和語意索引元件安裝在目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。<br /><br /> 1 = 已安裝全文檢索和語意索引元件。<br /><br /> 0 = 未安裝全文檢索和語意索引元件。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料類型：**int**|  
|IsHadrEnabled|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更新版本。<br /><br /> 在這個伺服器執行個體上已啟用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。<br /><br /> 0 = [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 功能已停用。<br /><br /> 1 = [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 功能已啟用。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料類型：**int**<br /><br /> 若要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體上建立及執行可用性複本，必須在此伺服器執行個體上啟用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。 如需詳細資訊，請參閱[啟用和停用 AlwaysOn 可用性群組 (SQL Server)](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)。<br /><br /> **注意：** IsHadrEnabled 屬性只與 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 相關。 此伺服器屬性不影響其他高可用性或災害復原功能，例如資料庫鏡像或記錄傳送。|  
|IsIntegratedSecurityOnly|伺服器處於整合式安全性模式。<br /><br /> 1 = 整合式安全性 (Windows 驗證)<br /><br /> 0 = 非整合式安全性。 (Windows 驗證及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證)。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料類型：**int**|  
|IsLocalDB|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更新版本。<br /><br /> 伺服器是 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] LocalDB 的執行個體。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。|  
|IsPolyBaseInstalled|**適用於**： [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 傳回伺服器執行個體是否已安裝 PolyBase 功能。<br /><br /> 0 = 未安裝 PolyBase。<br /><br /> 1 = 已安裝 PolyBase。<br /><br /> 基底資料類型：**int**|  
|IsSingleUser|伺服器處於單一使用者模式。<br /><br /> 1 = 單一使用者。<br /><br /> 0 = 非單一使用者<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料類型：**int**|  
|IsXTPSupported|**適用於**：SQL Server ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本)、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]。<br /><br /> 伺服器支援 In-Memory OLTP。<br /><br /> 1= 伺服器支援 In-Memory OLTP。<br /><br /> 0= 伺服器不支援 In-Memory OLTP。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料類型：**int**|  
|LCID|Windows 的定序地區設定識別碼 (LCID)。<br /><br /> 基底資料類型：**int**|  
|LicenseType|未使用的。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產品未保留或維護的授權資訊。 一律傳回 DISABLED。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|MachineName|執行伺服器執行個體的 Windows 電腦名稱。<br /><br /> 如果是叢集執行個體，也就是在 Microsoft Cluster Service 虛擬伺服器上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，便會傳回虛擬伺服器名稱。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|NumLicenses|未使用的。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產品未保留或維護的授權資訊。 一律傳回 NULL。<br /><br /> 基底資料類型：**int**|  
|ProcessID|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的處理序識別碼。 在識別哪個 Sqlservr.exe 屬於這個執行個體時，ProcessID 非常有用。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。<br /><br /> 基底資料類型：**int**|  
|ProductBuild|**適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (自 2015 年 10 月開始)。<br /><br /> 組建編號。|  
|ProductBuildType|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至目前版本 (從 2015 晚期開始的更新)。<br /><br /> 目前組建的組建類型。<br /><br /> 傳回下列項目之一：<br /><br /> OD = 特定客戶的隨選版本。<br /><br /> GDR = 透過 Windows Update 發行的一般發行版本。<br /><br /> NULL<br />= 不適用。|  
|ProductLevel|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的版本層級。<br /><br /> 傳回下列項目之一：<br /><br /> 'RTM' = 原始發行版本<br /><br /> 'SP*n*' = Service Pack 版本<br /><br /> 'CTP*n*', = Community Technical Preview 版本<br /><br /> 基底資料型別：**nvarchar(128)**|  
|ProductMajorVersion|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至目前版本 (從 2015 晚期開始的更新)。<br /><br /> 主要版本。|  
|ProductMinorVersion|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至目前版本 (從 2015 晚期開始的更新)。<br /><br /> 次要版本。|  
|ProductUpdateLevel|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至目前版本 (從 2015 晚期開始的更新)。<br /><br /> 目前組建的更新層級。 CU 表示累積更新。<br /><br /> 傳回下列項目之一：<br /><br /> CU*n* = 累積更新<br /><br /> NULL<br />= 不適用。|  
|ProductUpdateReference|**適用對象**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至目前版本 (從 2015 晚期開始的更新)。<br /><br /> 該版本的知識庫文章。|  
|ProductVersion|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的版本，格式為 '*major.minor.build.revision*'。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|ResourceLastUpdateDateTime|傳回資源資料庫上次更新的日期和時間。<br /><br /> 基底資料型別：**datetime**|  
|ResourceVersion|傳回版本資源資料庫。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|ServerName|指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體所關聯的 Windows 伺服器和執行個體資訊。<br /><br /> NULL = 輸入無效，或發生錯誤。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|SqlCharSet|定序識別碼中的 SQL 字元集識別碼。<br /><br /> 基底資料型別：**tinyint**|  
|SqlCharSetName|定序中的 SQL 字元集名稱。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|SqlSortOrder|定序中的 SQL 排序順序識別碼<br /><br /> 基底資料型別：**tinyint**|  
|SqlSortOrderName|定序中的 SQL 排序次序名稱。<br /><br /> 基底資料型別：**nvarchar(128)**|  
|FilestreamShareName|FILESTREAM 所使用之共用的名稱。<br /><br /> NULL = 輸入無效、發生錯誤或不適用。|  
|FilestreamConfiguredLevel|已設定的 FILESTREAM 存取層級。 如需詳細資訊，請參閱[檔案資料流存取層級](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md)。|  
|FilestreamEffectiveLevel|有效的 FILESTREAM 存取層級。 如果此層級已變更而且執行個體重新啟動或電腦重新啟動已暫止，這個值就可能會與 FilestreamConfiguredLevel 不同。 如需詳細資訊，請參閱[檔案資料流存取層級](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md)。|  
  
## <a name="return-types"></a>傳回類型  

**sql_variant**
  
## <a name="remarks"></a>Remarks  
  
### <a name="servername-property"></a>ServerName 屬性

`SERVERPROPERTY` 函式的 `ServerName` 屬性及 [@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md) 會傳回類似的資訊。 `ServerName` 屬性提供共同組成唯一伺服器執行個體的 Windows 伺服器和執行個體名稱。 [@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md) 提供目前設定的本機伺服器名稱。  
  
如果安裝時的預設伺服器名稱沒有變更，`ServerName` 屬性和 [@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md) 會傳回相同的資訊。 您可以執行下列作業來設定本機伺服器名稱：  
  
```sql
EXEC sp_dropserver 'current_server_name';  
GO  
EXEC sp_addserver 'new_server_name', 'local';  
GO  
```  
  
如果本機伺服器名稱已變更為不是安裝時的預設伺服器名稱，[@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md) 就會傳回新的名稱。  
  
### <a name="version-properties"></a>Version 屬性

`SERVERPROPERTY` 函式會傳回與版本資訊相關的個別屬性，而 [@@VERSION](../../t-sql/functions/version-transact-sql-configuration-functions.md) 函式則會將輸出結合成一個字串。 若您的應用程式需要個別屬性字串，您可以使用 `SERVERPROPERTY` 函式傳回它們，而非剖析 [@@VERSION](../../t-sql/functions/version-transact-sql-configuration-functions.md) 的結果。  

## <a name="permissions"></a>權限

所有使用者都可以查詢伺服器屬性。
  
## <a name="examples"></a>範例

下列範例會使用 `SELECT` 陳述式中的 `SERVERPROPERTY` 函式來傳回目前 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 執行個體的相關資訊。
  
```sql
SELECT  
  SERVERPROPERTY('MachineName') AS ComputerName,
  SERVERPROPERTY('ServerName') AS InstanceName,  
  SERVERPROPERTY('Edition') AS Edition,
  SERVERPROPERTY('ProductVersion') AS ProductVersion,  
  SERVERPROPERTY('ProductLevel') AS ProductLevel;  
GO  
```  
  
## <a name="see-also"></a>另請參閱

[SQL Server 2016 的版本和元件](../../sql-server/editions-and-components-of-sql-server-2016.md)  
