---
title: sys.dm_db_task_space_usage (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_task_space_usage_TSQL
- sys.dm_db_task_space_usage_TSQL
- dm_db_task_space_usage
- sys.dm_db_task_space_usage
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_task_space_usage dynamic management view
ms.assetid: fb0c87e5-43b9-466a-a8df-11b3851dc6d0
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 14dc454396c7a54e97cc207a02a1b3f9ac83bf4f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmdbtaskspaceusage-transact-sql"></a>sys.dm_db_task_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回資料庫工作的頁面配置及取消配置活動。  
  
> [!NOTE]  
>  這個檢視只會套用於[tempdb 資料庫](../../relational-databases/databases/tempdb-database.md)。  
  
> [!NOTE]  
>  若要呼叫從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名稱**sys.dm_pdw_nodes_db_task_space_usage**。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|工作階段識別碼。|  
|**request_id**|**int**|工作階段內的要求識別碼。<br /><br /> 要求也叫作批次，可包含一或多項查詢。 一個工作階段可以同時有多項作用中要求。 如果使用平行執行計畫，則要求中的每一項查詢可啟動多個執行緒 (工作)。|  
|**exec_context_id**|**int**|工作的執行內容識別碼。 如需詳細資訊，請參閱[sys.dm_os_tasks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)。|  
|**database_id**|**smallint**|資料庫識別碼。|  
|**user_objects_alloc_page_count**|**bigint**|這項工作所保留或配置給使用者物件的頁數。|  
|**user_objects_dealloc_page_count**|**bigint**|這項工作已取消配置且不再保留給使用者物件的頁數。|  
|**internal_objects_alloc_page_count**|**bigint**|這項工作所保留或配置給內部物件的頁數。|  
|**internal_objects_dealloc_page_count**|**bigint**|這項工作已取消配置且不再保留給內部物件的頁數。|  
|**pdw_node_id**|**int**|**適用於**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此發行版本上的節點識別碼。|  
  
## <a name="permissions"></a>Permissions

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`資料庫的權限。   

## <a name="remarks"></a>備註  
 IAM 頁面不包括在這份檢視所報告的任何頁面計數中。  
  
 在要求開始時，頁面計數器會初始化為零 (0)。 這些值會在要求完成時在工作階段層級上彙總。 如需詳細資訊，請參閱[sys.dm_db_session_space_usage & #40;TRANSACT-SQL & #41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md).  
  
 工作資料表快取、暫存資料表快取和延遲卸除作業，會影響在指定工作中配置和取消配置的頁數。  
  
## <a name="user-objects"></a>使用者物件  
 下列物件已包括在使用者物件頁面計數器中：  
  
-   使用者自訂資料表和索引  
  
-   系統資料表和索引  
  
-   全域暫存資料表和索引  
  
-   本機暫存資料表和索引  
  
-   資料表變數  
  
-   資料表值函式中傳回的資料表  
  
## <a name="internal-objects"></a>內部物件  
 內部物件只在比較**tempdb**。 下列物件已包括在內部物件頁面計數器中：  
  
-   用於資料指標或多工緩衝處理作業和暫存大型物件 (LOB) 儲存體的工作資料表  
  
-   用於如雜湊聯結等作業的工作檔案  
  
-   排序執行  
  
## <a name="physical-joins"></a>實體聯結  
 ![Sys.dm_db_session_task_usage 的](../../relational-databases/system-dynamic-management-views/media/join-dm-db-task-space-usage-1.gif "的 sys.dm_db_session_task_usage 的實體聯結")  
  
## <a name="relationship-cardinalities"></a>關聯性基數  
  
|來源|若要|關聯性|  
|----------|--------|------------------|  
|dm_db_task_space_usage.request_id|dm_exec_requests.request_id|一對一|  
|dm_db_task_space_usage.session_id|dm_exec_requests.session_id|一對一|  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [與資料庫相關動態管理檢視&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_os_tasks &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)   
 [sys.dm_db_file_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  


