---
title: sys.dm_exec_query_memory_grants (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_memory_grants_TSQL
- sys.dm_exec_query_memory_grants
- sys.dm_exec_query_memory_grants_TSQL
- dm_exec_query_memory_grants
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_memory_grants dynamic management view
ms.assetid: 2c417747-2edd-4e0d-8a9c-e5f445985c1a
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5ea497514e558ab362429c3c8dda880fd41570df
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexecquerymemorygrants-transact-sql"></a>sys.dm_exec_query_memory_grants (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回已要求並等待記憶體授與或獲得記憶體授與所有查詢的相關資訊。 不需要記憶體授權的查詢不會出現在此檢視中。 例如，排序和雜湊聯結作業可能會有記憶體授權來執行查詢，查詢是否正確時**ORDER BY**子句不會授與的記憶體。  
  
 在 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]，動態管理檢視不可以公開可能會影響資料庫內含項目的資訊或公開有關使用者可存取之其他資料庫的資訊。 為了避免公開此資訊，包含不屬於連接租用戶之資料的每個資料列都會被篩選出來。此外，資料行的值**scheduler_id**， **wait_order**， **pool_id**， **group_id**會篩選出來; 資料行值設定為 NULL。  
  
> [!NOTE]  
>  若要呼叫從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名稱**sys.dm_pdw_nodes_exec_query_memory_grants**。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|執行此查詢的工作階段識別碼 (SPID)。|  
|**request_id**|**int**|要求的識別碼。 在工作階段的內容中是唯一的。|  
|**scheduler_id**|**int**|排程此查詢的排程器識別碼。|  
|**dop**|**smallint**|此查詢之平行處理原則的程度。|  
|**request_time**|**datetime**|此查詢要求記憶體授權的日期和時間。|  
|**grant_time**|**datetime**|授與記憶體給此查詢的日期和時間。 如果尚未授與記憶體，則為 NULL。|  
|**requested_memory_kb**|**bigint**|要求的記憶體總數 (以 KB 為單位)。|  
|**granted_memory_kb**|**bigint**|實際授與的記憶體總數 (以 KB 為單位)。 如果尚未授與記憶體，則可能為 NULL。 一般情況，這個值應該是相同**requested_memory_kb**。 對於索引建立，除了一開始授與的記憶體之外，伺服器還可以視需求額外授與記憶體。|  
|**required_memory_kb**|**bigint**|執行此查詢所需的記憶體下限 (以 KB 為單位)。 **requested_memory_kb**相同或大於此數量。|  
|**used_memory_kb**|**bigint**|目前使用的實體記憶體 (以 KB 為單位)。|  
|**max_used_memory_kb**|**bigint**|到目前為止使用的最大實體記憶體 (以 KB 為單位)。|  
|**query_cost**|**float**|估計的查詢成本。|  
|**timeout_sec**|**int**|此查詢放棄記憶體授權要求之前的逾時秒數。|  
|**resource_semaphore_id**|**smallint**|此查詢正在等候之資源信號的非唯一識別碼。<br /><br /> **注意：**此識別碼是唯一的版本中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之前[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]。 這項變更可以影響疑難排解的查詢執行。 如需詳細資訊，請參閱本主題後面的＜備註＞一節。|  
|**queue_id**|**smallint**|此查詢等候記憶體授權時所在的等候中佇列識別碼。 如果已經授與記憶體，則為 NULL。|  
|**wait_order**|**int**|等候中查詢內指定的連續順序**queue_id**。 如果其他查詢取得記憶體授權或逾時，則給定查詢的此值可能會變更。如果已經授與記憶體，則為 NULL。|  
|**is_next_candidate**|**bit**|下一個記憶體授權的候選。<br /><br /> 1 = 是<br /><br /> 0 = 否<br /><br /> NULL = 已經授與記憶體。|  
|**wait_time_ms**|**bigint**|等候時間 (以毫秒為單位)。 如果已經授與記憶體，則為 NULL。|  
|**plan_handle**|**varbinary(64)**|此查詢計畫的識別碼。 使用**sys.dm_exec_query_plan**來擷取實際的 XML 計畫。|  
|**sql_handle**|**varbinary(64)**|此查詢的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文字識別碼。 使用**sys.dm_exec_sql_text**取得實際[!INCLUDE[tsql](../../includes/tsql-md.md)]文字。|  
|**group_id**|**int**|這個查詢執行所在工作負載群組的識別碼。|  
|**pool_id**|**int**|這個工作負載群組所屬資源集區的識別碼。|  
|**is_small**|**tinyint**|設定為 1 時，表示此授與使用小型資源信號。 設定為 0 時，表示使用一般信號。|  
|**ideal_memory_kb**|**bigint**|授與的記憶體大小 (以 KB 為單位)，可將所有東西配置到實體記憶體。 這是以基數估計值為基礎。|  
|**pdw_node_id**|**int**|**適用於**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此發行版本上的節點識別碼。|  
  
## <a name="permissions"></a>Permissions  

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`資料庫的權限。   
   
## <a name="remarks"></a>備註  
 查詢逾時的一般偵錯狀況可能如下所示：  
  
-   檢查整體系統記憶體狀態使用[sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)， [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)，以及各種效能計數器。  
  
-   檢查查詢執行記憶體中的保留項目**sys.dm_os_memory_clerks**其中`type = 'MEMORYCLERK_SQLQERESERVATIONS'`。  
  
-   檢查等候授權使用的查詢**sys.dm_exec_query_memory_grants**。  
  
    ```  
    --Find all queries waiting in the memory queue  
    SELECT * FROM sys.dm_exec_query_memory_grants where grant_time is null  
    ```  
  
-   使用的記憶體授與使用的搜尋查詢的快取[sys.dm_exec_cached_plans &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)和[sys.dm_exec_query_plan &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)  
  
    ```  
    -- retrieve every query plan from the plan cache  
    USE master;  
    GO  
    SELECT * FROM sys.dm_exec_cached_plans cp CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);  
    GO  
  
    ```  
  
-   進一步檢查需要大量記憶體的查詢使用[sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)。  
  
    ```  
    --Find top 5 queries by average CPU time  
    SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
    Plan_handle, query_plan   
    FROM sys.dm_exec_query_stats AS qs  
    CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle)  
    ORDER BY total_worker_time/execution_count DESC;  
    GO  
  
    ```  
  
-   如果懷疑有失控查詢，檢查從 Showplan [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)與批次中的文字[sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)。  
  
 使用包含 ORDER BY 或彙總之動態管理檢視的查詢，有可能會增加記憶體耗用量，但也因此可協助它們正在進行疑難排解的問題。  
  
 資源管理員功能可讓資料庫管理員在資源集區間散發伺服器資源，最多可達 64 個集區。 開頭為[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]，每個集區的行為都像是一個小型的獨立伺服器執行個體，而且需要 2 個信號。 從傳回的資料列數目**sys.dm_exec_query_resource_semaphores**可以是 20 倍以上的資料列中傳回[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [sys.dm_exec_query_resource_semaphores &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql.md)   
 [執行相關動態管理檢視和函數&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


