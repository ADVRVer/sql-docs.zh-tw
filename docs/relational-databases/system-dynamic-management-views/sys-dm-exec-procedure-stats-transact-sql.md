---
title: sys.databases dm_exec_procedure_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/03/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats
- sys.dm_exec_procedure_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_procedure_stats dynamic management view
ms.assetid: ab8ddde8-1cea-4b41-a7e4-697e6ddd785a
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9c180e31958c6d1a6c9cdd728de5ea9a2e6b32ba
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734783"
---
# <a name="sysdm_exec_procedure_stats-transact-sql"></a>sys.dm_exec_procedure_stats (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asdw-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  傳回快取預存程序的彙總效能統計資料。 此檢視會針對每個快取預存程序計畫傳回一個資料列，而且資料列的存留期間與預存程序維持快取狀態的時間一樣長。 從快取中移除預存程序時，對應的資料列也會從這個檢視中刪除。 此時，就會引發效能統計資料 SQL 追蹤事件 (與 **sys.dm_exec_query_stats** 很相似)。  
  
 在 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]，動態管理檢視不可以公開可能會影響資料庫內含項目的資訊或公開有關使用者可存取之其他資料庫的資訊。 為避免公開此資訊，包含不屬於連接租使用者之資料的每個資料列都會被篩選掉。  
  
> [!NOTE]
> **Dm_exec_procedure_stats**的結果可能會隨著每次執行而不同，因為資料只會反映完成的查詢，而不是仍在進行中的查詢。
> 若要從或呼叫此 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ，請使用**dm_pdw_nodes_exec_procedure_stats**的名稱。 

  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------| 
|**database_id**|**int**|預存程序所在的資料庫識別碼。|  
|object_id|**int**|預存程序的物件識別碼。|  
|**type**|**char(2)**|物件的類型：<br /><br /> P = SQL 預存程序<br /><br /> PC = 組件 (CLR) 預存程序<br /><br /> X = 擴充預存程序|  
|**type_desc**|**nvarchar(60)**|物件類型的描述：<br /><br /> SQL_STORED_PROCEDURE<br /><br /> CLR_STORED_PROCEDURE<br /><br /> EXTENDED_STORED_PROCEDURE|  
|**sql_handle**|**varbinary(64)**|這可以用來與從這個預存程式中執行的**dm_exec_query_stats**中的查詢相互關聯。|  
|**plan_handle**|**varbinary(64)**|記憶體中計畫的識別碼。 這個識別碼是暫時性的，只有當計畫留在快取時才會保留。 這個值可與**sys.databases dm_exec_cached_plans**動態管理檢視搭配使用。<br /><br /> 當原生編譯的預存程序查詢記憶體最佳化的資料表時，一律為 0x000。|  
|**cached_time**|**datetime**|在快取中加入預存程序的時間。|  
|**last_execution_time**|**datetime**|上次執行預存程序的時間。|  
|**execution_count**|**bigint**|預存程式自上次編譯以來執行的次數。|  
|**total_worker_time**|**bigint**|這個預存程式在編譯以來執行所耗用的 CPU 時間總量（以微秒為單位）。<br /><br /> 如果原生編譯預存程序執行數次的時間都少於 1 毫秒， **total_worker_time** 可能就不準確。|  
|**last_worker_time**|**bigint**|預存程序上次執行所耗用的 CPU 時間 (以微秒為單位)。 <sup>1</sup>|  
|**min_worker_time**|**bigint**|這個預存程式在單次執行期間曾耗用的最小 CPU 時間（以微秒為單位）。 <sup>1</sup>|  
|**max_worker_time**|**bigint**|這個預存程式在單次執行期間曾耗用的最大 CPU 時間（以微秒為單位）。 <sup>1</sup>|  
|**total_physical_reads**|**bigint**|這個預存程式在編譯以來執行所執行的實體讀取總數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**last_physical_reads**|**bigint**|上次執行預存程式時所執行的實體讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**min_physical_reads**|**bigint**|這個預存程式在單次執行期間曾執行的最小實體讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**max_physical_reads**|**bigint**|這個預存程式在單次執行期間曾執行的最大實體讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**total_logical_writes**|**bigint**|這個預存程式在編譯以來執行所執行的邏輯寫入總數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**last_logical_writes**|**bigint**|上次執行計畫時變動的緩衝集區頁面數目。 如果已修改頁面，則不會計算寫入。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**min_logical_writes**|**bigint**|這個預存程式在單次執行期間曾執行的最小邏輯寫入數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**max_logical_writes**|**bigint**|這個預存程式在單次執行期間曾執行的最大邏輯寫入數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**total_logical_reads**|**bigint**|這個預存程式在編譯以來執行所執行的邏輯讀取總數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**last_logical_reads**|**bigint**|上次執行預存程式時，所執行的邏輯讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**min_logical_reads**|**bigint**|這個預存程式在單次執行期間曾執行的最小邏輯讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**max_logical_reads**|**bigint**|這個預存程式在單次執行期間曾執行的最大邏輯讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**total_elapsed_time**|**bigint**|這個預存程式已完成執行的總時間（以微秒為單位）。|  
|**last_elapsed_time**|**bigint**|這個預存程式最近完成執行所經過的時間（以微秒為單位）。|  
|**min_elapsed_time**|**bigint**|這個預存程式已完成執行的最小經過時間（以微秒為單位）。|  
|**max_elapsed_time**|**bigint**|這個預存程式已完成執行的最大經過時間（以微秒為單位）。|  
|**total_spills**|**bigint**|這個預存程式在編譯以來執行所溢出的總頁數。<br /><br /> **適用于**：從 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3 開始|  
|**last_spills**|**bigint**|上次執行預存程式時所溢出的頁面數目。<br /><br /> **適用于**：從 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3 開始|  
|**min_spills**|**bigint**|這個預存程式在單次執行期間曾溢出的最小頁數。<br /><br /> **適用于**：從 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3 開始|  
|**max_spills**|**bigint**|這個預存程式在單次執行期間曾發生過的最大頁面數目。<br /><br /> **適用于**：從 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3 開始|  
|**pdw_node_id**|**int**|此散發所在節點的識別碼。<br /><br />**適用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
|**total_page_server_reads**|**bigint**|這個預存程式在編譯以來執行所執行的頁面伺服器讀取總數。<br /><br /> **適用于**： Azure SQL Database 超大規模資料庫|  
|**last_page_server_reads**|**bigint**|上次執行預存程式時，所執行的頁面伺服器讀取數目。<br /><br /> **適用于**： Azure SQL Database 超大規模資料庫|  
|**min_page_server_reads**|**bigint**|這個預存程式在單次執行期間曾執行的頁面伺服器讀取次數下限。<br /><br /> **適用于**： Azure SQL Database 超大規模資料庫|  
|**max_page_server_reads**|**bigint**|這個預存程式在單次執行期間曾執行的最大頁面伺服器讀取數。<br /><br /> **適用于**： Azure SQL Database 超大規模資料庫|  
  
 <sup>1</sup>在啟用統計資料收集時，原生編譯預存程式會收集工作者時間（以毫秒為單位）。 若查詢的執行時間少於一毫秒，其值將會是 0。  
  
## <a name="permissions"></a>權限  

在上 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ，需要 `VIEW SERVER STATE` 許可權。   
在高階 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 層級上，需要 `VIEW DATABASE STATE` 資料庫的許可權。 在 [ [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 標準] 和 [基本] 層上，需要**伺服器管理員**或**Azure Active Directory 系統管理員**帳戶。   
   
## <a name="remarks"></a>備註  
 預存程序執行完成時，就會更新檢視中的統計資料。  
  
## <a name="examples"></a>範例  
 下列範例會傳回平均經過時間所識別之前 10 項預存程序的相關資訊。  
  
```sql  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'proc name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_procedure_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>另請參閱  
[執行相關的動態管理檢視和函數 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
[dm_exec_sql_text &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
[dm_exec_query_plan &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[dm_exec_query_stats &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)    
[dm_exec_trigger_stats &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)    
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  
  


