---
title: sys.databases pdw_loader_backup_runs （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2b72034c-6a11-46b9-a76c-7a88b2bea360
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c8e7826e4dcefdbed65fb0fa1f3368411a9ef12a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68127474"
---
# <a name="syspdw_loader_backup_runs-transact-sql"></a>sys.databases pdw_loader_backup_runs （Transact-sql）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  包含在中進行中[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]和已完成之備份和還原作業的相關資訊，以及中的進行中和已完成[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]的備份、還原和載入作業。 此資訊在系統重新啟動之後會持續存留。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|特定備份、還原或負載執行的唯一識別碼。<br /><br /> 此視圖的索引鍵。||  
|NAME|**nvarchar(255)**|若為 load，則為 Null。 備份或還原的選擇性名稱。||  
|submit_time|**datetime**|提交要求的時間。||  
|start_time|**datetime**|作業開始的時間。||  
|end_time|**datetime**|作業完成、失敗或已取消的時間。||  
|total_elapsed_time|**int**|Start_time 與目前時間之間的時間總計，或 start_time 與 end_time，已完成、已取消或失敗的執行之間。|如果 total_elapsed_time 超過整數的最大值（以毫秒為單位的24.8 天），則會造成具體化失敗，因為溢位。<br /><br /> 最大值（以毫秒為單位）相當於24.8 天。|  
|operation_type|**Nvarchar （16）**|載入類型。|「備份」、「載入」、「還原」|  
|模式|**Nvarchar （16）**|執行類型中的模式。|針對 operation_type =**備份**<br />**差異**<br />**寫**<br /><br /> 針對 operation_type =**載入**<br />**追加**<br />**刷新**<br />**UPSERT**<br /><br /> 針對 operation_type =**還原**<br />**DATABASE**<br />**HEADER_ONLY**|  
|database_name|**nvarchar(255)**|這項作業之內容的資料庫名稱||  
|table_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Principal_id|**int**|要求操作之使用者的識別碼。||  
|session_id|**Nvarchar （32）**|執行作業之會話的識別碼。|請參閱[dm_pdw_exec_sessions &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)中的 session_id。|  
|request_id|**Nvarchar （32）**|執行作業之要求的識別碼。 若為 load，這就是目前或最後一個與此載入相關聯的要求。|請參閱[dm_pdw_exec_requests &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)中的 request_id。|  
|status|**Nvarchar （16）**|執行的狀態。|「已取消」、「已完成」、「失敗」、「已排入佇列」、「執行中」|  
|progress|**int**|完成百分比。|0 到 100|  
|命令|**nvarchar(4000)**|使用者所提交之命令的全文檢索。|如果超過4000個字元（計算空格），將會被截斷。|  
|rows_processed|**Bigint**|這項作業中處理的資料列數目。||  
|rows_rejected|**Bigint**|此作業中拒絕的資料列數目。||  
|rows_inserted|**Bigint**|在這項作業中插入資料庫資料表的資料列數目。||  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲目錄檢視](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
