---
title: sys.event_log (Azure SQL Database) |Microsoft 文件
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- event_log
- sys.event_log_TSQL
- event_log_TSQL
- sys.event_log
dev_langs:
- TSQL
helpviewer_keywords:
- event_log
- sys.event_log
ms.assetid: ad5496b5-e5c7-4a18-b5a0-3f985d7c4758
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 5f871501b63bd9823c5a44872224439e8df07a9c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33182534"
---
# <a name="syseventlog-azure-sql-database"></a>sys.event_log (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  傳回成功[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]資料庫連線、 連線失敗和死結。 您可以使用這項資訊追蹤 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 的資料庫活動或進行疑難排解。  
  
> [!CAUTION]  
>  安裝具有大量的資料庫或登入數高，sys.event_log 的活動可以造成效能降低，高 CPU 使用量，限制，並可能會導致登入失敗。 Sys.event_log 的查詢可以協助的問題。 Microsoft 正在以解決此問題。 在此同時，若要減少此問題的影響，限制 sys.event_log 的查詢。 區 SQL Server 外掛程式的使用者應該瀏覽[Microsoft Azure SQL Database 外掛程式微調 （& s） 效能調整](https://discuss.newrelic.com/t/microsoft-azure-sql-database-plugin-tuning-performance-tweaks/30729)的額外組態資訊。  
  
 `sys.event_log`檢視包含下列資料行。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|資料庫的名稱。 如果連接失敗且使用者未指定資料庫名稱，則這個資料行會是空白。|  
|**start_time**|**datetime2**|彙總間隔開始的 UTC 日期和時間。 對於彙總的事件，這個時間永遠是 5 分鐘的倍數。 例如：<br /><br /> '2011-09-28 16:00:00'<br />'2011-09-28 16:05:00'<br />'2011-09-28 16:10:00'|  
|**end_time**|**datetime2**|彙總間隔結束的 UTC 日期和時間。 彙總的事件，如**End_time**一律會多出剛好 5 分鐘比對應**start_time**相同的資料列中。 事件未彙總， **start_time**和**end_time**等於實際的 UTC 日期和時間的事件。|  
|**event_category**|**nvarchar(64)**|產生這個事件的高階元件。<br /><br /> 請參閱[事件類型](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes)取得一份可能的值。|  
|**event_type**|**nvarchar(64)**|事件的類型。<br /><br /> 請參閱[事件類型](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes)取得一份可能的值。|  
|**event_subtype**|**int**|所發生事件的子類型。<br /><br /> 請參閱[事件類型](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes)取得一份可能的值。|  
|**event_subtype_desc**|**nvarchar(64)**|事件子類型的描述。<br /><br /> 請參閱[事件類型](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes)取得一份可能的值。|  
|**severity**|**int**|錯誤的嚴重性。 可能的值為：<br /><br /> 0 = 資訊<br />1 = 警告<br />2 = 錯誤|  
|**event_count**|**int**|發生此事件的次數指定的資料庫指定的時間間隔內 (**start_time**和**end_time**)。|  
|**描述**|**nvarchar(max)**|事件的詳細描述。<br /><br /> 請參閱[事件類型](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes)取得一份可能的值。|  
|**additional_data**|**XML**|*注意： 這個值一律為 Azure SQL Database V12 為 NULL。請參閱[範例](#Deadlock)一節以取得如何擷取適用於 V12 死結事件。*<br /><br /> 如**死結**事件，這個資料行會包含死結圖表。 對於其他事件類型，這個資料行為 NULL。 |  
  
##  <a name="EventTypes"></a> 事件類型  
 在此檢視中的每個資料列所記錄的事件所識別的類別 (**event_category**)，事件類型 (**event_type**)，和子類型 (**event_subtype**)。 下表列出這個檢視中所收集事件的類型。  
  
 中的事件**連線**分類中，會提供摘要資訊，sys.database_connection_stats 檢視中。  
  
> [!NOTE]  
>  這個檢視不包括所有可能發生的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 資料庫事件，只包括這裡列出的事件。 其他類別目錄、事件類型和子類型會在未來的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 版本中加入。  
  
|**event_category**|**event_type**|**event_subtype**|**event_subtype_desc**|**severity**|**描述**|  
|-------------------------|---------------------|------------------------|------------------------------|------------------|---------------------|  
|**連線能力**|**connection_successful**|0|**connection_successful**|0|已成功連接資料庫。|  
|**連線能力**|**connection_failed**|0|**invalid_login_name**|2|登入名稱在這個版本的 SQL Server 中無效。|  
|**連線能力**|**connection_failed**|1|**windows_auth_not_supported**|2|這個版本的 SQL Server 不支援 Windows 登入。|  
|**連線能力**|**connection_failed**|2|**attach_db_not_supported**|2|使用者要求附加不支援的資料庫檔案。|  
|**連線能力**|**connection_failed**|3|**change_password_not_supported**|2|不支援使用者要求變更使用者登入的密碼。|  
|**連線能力**|**connection_failed**|4|**login_failed_for_user**|2|使用者登入失敗。|  
|**連線能力**|**connection_failed**|5|**login_disabled**|2|登入已停用。|  
|**連線能力**|**connection_failed**|6|**failed_to_open_db**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 資料庫無法開啟。 可能原因是資料庫不存在，或缺少開啟資料庫的驗證。|  
|**連線能力**|**connection_failed**|7|**blocked_by_firewall**|2|不允許用戶端 IP 位址存取伺服器。|  
|**連線能力**|**connection_failed**|8|**client_close**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 用戶端可能在建立連接時逾時。 嘗試建立連接時發生逾時。|  
|**連線能力**|**connection_failed**|9|**重新設定**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 連接失敗，因為資料庫當時正在進行重新組態。|  
|**連線能力**|**connection_terminated**|0|**idle_connection_timeout**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 連接已閒置超過系統定義的臨界值。|  
|**連線能力**|**connection_terminated**|1|**重新設定**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 由於資料庫重新設定，已終止工作階段。|  
|**連線能力**|**節流設定**|*\<原因碼 >*|**reason_code**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 要求已節流。  節流原因代碼： *\<原因碼 >*。 如需詳細資訊，請參閱[引擎節流](http://msdn.microsoft.com/library/windowsazure/dn338079.aspx)。|  
|**連線能力**|**throttling_long_transaction**|40549|**long_transaction**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 工作階段已終止，因為您有長時間執行的交易。 請嘗試縮短您的交易。 如需詳細資訊，請參閱[資源限制](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx)。|  
|**連線能力**|**throttling_long_transaction**|40550|**excessive_lock_usage**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 已終止工作階段，因為它取得太多鎖定。 請嘗試在單一交易中讀取或修改較少的資料列。 如需詳細資訊，請參閱[資源限制](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx)。|  
|**連線能力**|**throttling_long_transaction**|40551|**excessive_tempdb_usage**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 已終止工作階段，因為它過度使用 TEMPDB。 請嘗試修改查詢，減少使用暫存資料表空間。 如需詳細資訊，請參閱[資源限制](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx)。|  
|**連線能力**|**throttling_long_transaction**|40552|**excessive_log_space_usage**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 已終止工作階段，因為它過度使用交易記錄檔空間。 請嘗試在單一交易中修改較少的資料列。 如需詳細資訊，請參閱[資源限制](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx)。|  
|**連線能力**|**throttling_long_transaction**|40553|**excessive_memory_usage**|2|*注意： 僅適用於 Azure SQL Database V11。*<br /><br /> 已終止工作階段，因為它過度使用記憶體。 請嘗試修改查詢以處理較少的資料列。 如需詳細資訊，請參閱[資源限制](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx)。|  
|**引擎**|**死結**|0|**死結**|2|發生死結。|  
  
## <a name="permissions"></a>Permissions  
 具有存取權限的使用者**主要**資料庫有唯讀存取此檢視。  
  
## <a name="remarks"></a>備註  
  
### <a name="event-aggregation"></a>事件彙總  
 這個檢視的事件資訊會在 5 分鐘間隔內收集和彙總。 **Event_count**資料行代表特殊次數**event_type**和**event_subtype**給定的時間間隔內發生特定資料庫。  
  
> [!NOTE]  
>  某些事件不會彙總，像是死結。 對於這些事件， **event_count**將會是 1 和**start_time**和**end_time**將等於實際的 UTC 日期和時間的事件發生時。  
  
 例如，如果使用者因為登入名稱無效，而在連接到 Database1 資料庫時於 2012 年 2 月 5 日 11:00 到 11:05 (UTC) 之間失敗七次，這項資訊會在這個檢視的單一資料列中提供：  
  
|**database_name**|**start_time**|**end_time**|**event_category**|**event_type**|**event_subtype**|**event_subtype_desc**|**severity**|**event_count**|**描述**|**additional_data**|  
|------------------------|---------------------|-------------------|-------------------------|---------------------|------------------------|------------------------------|------------------|----------------------|---------------------|--------------------------|  
|`Database1`|`2012-02-05 11:00:00`|`2012-02-05 11:05:00`|`connectivity`|`connection_failed`|`4`|`login_failed_for_user`|`2`|`7`|`Login failed for user.`|`NULL`|  
  
### <a name="interval-starttime-and-endtime"></a>間隔的 start_time 和 end_time  
 在事件發生時，事件是否包含在彙總間隔*上*或*之後 * * * start_time** 和*之前 * * * end_time** 對於該間隔。 例如，正巧發生在 `2012-10-30 19:25:00.0000000` 的事件只會納入到以下所示的第二段間隔：  
  
```  
start_time                    end_time  
2012-10-30 19:20:00.0000000   2012-10-30 19:25:00.0000000  
2012-10-30 19:25:00.0000000   2012-10-30 19:30:00.0000000  
```  
  
### <a name="data-updates"></a>資料更新  
 這個檢視中的資料會累積一段時間。 通常資料會在彙總間隔開始的 1 小時內累積，但是最長可能需要 24 小時，所有資料才會出現在檢視中。 在這段期間，單一資料列內的資訊會定期更新。  
  
### <a name="data-retention"></a>資料保留  
 根據邏輯伺服器的資料庫數目以及每個資料庫所產生的唯一事件數目而定，這個檢視表中的資料最長會保留 30 天或以下。 若要保留這項資訊更長的時間，請將資料複製到另一個資料庫。 在您製作檢視的初始副本之後，檢視中的資料列可能會隨資料累積而更新。 為了讓資料副本保持最新狀態，請定期執行資料列的資料表掃描，查看現有資料列的事件計數是否增加，並且識別新資料列 (您可以使用開始和結束時間識別唯一資料列)，然後用這些變更來更新您的資料副本。  
  
### <a name="errors-not-included"></a>不包括錯誤  
 這個檢視可能不會包括所有連接和錯誤資訊：  
  
-   這個檢視不包括所有[!INCLUDE[ssSDS](../../includes/sssds-md.md)]資料庫可能發生的錯誤，只包括[事件類型](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes)本主題中。  
  
-   如果在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 資料中心內發生機器故障，則事件資料表中可能會遺漏邏輯伺服器的少量資料。  
  
-   如果已透過 DoSGuard 封鎖 IP 位址，則來自該 IP 位址的連接嘗試事件就無法收集，也不會出現在這個檢視中。  
  
## <a name="examples"></a>範例  
  
### <a name="simple-examples"></a>簡單範例  
 以下查詢會傳回 2011 年 9 月 25 日中午到 2011 年 9 月 28 日中午 (UTC) 之間發生的所有事件。 根據預設，查詢結果會依照**start_time** （遞增順序）。  
  
```  
SELECT * FROM sys.event_log   
WHERE start_time >= '2011-09-25:12:00:00'   
    AND end_time <= '2011-09-28 12:00:00';  
```  
  
 下列查詢會傳回 Database1 資料庫時 （僅適用於 Azure SQL Database V11） 的所有死結事件。  
  
```  
SELECT * FROM sys.event_log   
WHERE event_type = 'deadlock'   
    AND database_name = 'Database1';  
```  
<a name="Deadlock"></a> 下列查詢會傳回 Database1 資料庫時 （僅適用於 Azure SQL Database V12） 的所有死結事件。  
  
```  
WITH CTE AS (  
       SELECT CAST(event_data AS XML)  AS [target_data_XML]   
   FROM sys.fn_xe_telemetry_blob_target_read_file('dl', null, null, null)  
)  
SELECT target_data_XML.value('(/event/@timestamp)[1]', 'DateTime2') AS Timestamp,  
target_data_XML.query('/event/data[@name=''xml_report'']/value/deadlock') AS deadlock_xml,  
target_data_XML.query('/event/data[@name=''database_name'']/value').value('(/value)[1]', 'nvarchar(100)') AS db_name  
FROM CTE   
  
```  
  
  
 以下查詢會傳回 2011 年 9 月 25 日上午 10:00 到 11:00 (UTC) 之間在發生的 SQL 工作者執行緒事件上發生的硬節流。  
  
```  
SELECT * FROM sys.event_log   
WHERE event_type = 'throttling'   
    AND event_subtype = 4194307   
    AND start_time >= '2011-09-25 10:00:00'   
    AND end_time <= '2011-09-25 11:00:00';  
```  
  
### <a name="db-scoped-extended-event"></a>資料庫範圍擴充的事件  
 若要設定資料庫範圍擴充事件 (XEvent) 工作階段中使用下列範例程式碼：  
  
```sql  
IF EXISTS  
    (SELECT * from sys.database_event_sessions  
        WHERE name = 'azure_monitor_deadlock_session')  
BEGIN  
    ALTER EVENT SESSION azure_monitor_deadlock_session  
        ON DATABASE  
        DROP TARGET package0.ring_buffer;  
  
    DROP EVENT SESSION azure_monitor_deadlock_session  
        ON DATABASE;  
END  
  
CREATE EVENT SESSION azure_monitor_deadlock_session  
    ON DATABASE  
    ADD EVENT sqlserver.database_xml_deadlock_report  
    ADD TARGET package0.ring_buffer  
    (  
        SET max_memory = 2048, max_events_limit = 10  
    )  
    WITH (STARTUP_STATE = ON,  
          EVENT_RETENTION_MODE = ALLOW_SINGLE_EVENT_LOSS);  
  
ALTER EVENT SESSION azure_monitor_deadlock_session  
    ON DATABASE  
    STATE = START;  
```  
  
### <a name="check-for-deadlock"></a>檢查有死結

您可以使用下列查詢來檢查是否有死結。  
  
```sql  
WITH CTE AS (  
    SELECT CAST(xet.target_data AS XML)  AS [target_data_XML]  
        FROM            sys.dm_xe_database_session_targets AS xet  
             INNER JOIN sys.dm_xe_database_sessions        AS xe  
                 ON (xe.address = xet.event_session_address)  
        WHERE xe.name = 'azure_monitor_deadlock_session'  
)  
, CTE2 AS (  
    SELECT  
            T2.EventData.query('.').value(  
                '(/event/@timestamp)[1]', 'DateTime2') AS Timestamp,  
            T2.EventData.query('.').query(  
                '(/event/data/value/deadlock)[1]')     AS deadlock_xml  
        FROM CTE  
            CROSS Apply [target_data_XML].nodes(  
                '/RingBufferTarget/event') AS T2(EventData)  
)  
SELECT * FROM CTE2;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Azure SQL Database 中的擴充的事件](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
  
  
