---
title: sys.databases dm_pdw_dms_workers （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0a284d18-3c46-4ffa-bcc9-689e660ee8b4
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6e5f295637db0e138caf324e3126707b9e0ea774
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899494"
---
# <a name="sysdm_pdw_dms_workers-transact-sql"></a>sys.databases dm_pdw_dms_workers （Transact-sql）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  保存所有工作人員完成 DMS 步驟的相關資訊。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**Nvarchar （32）**|此 DMS 背景工作角色所屬的查詢。<br /><br /> request_id、step_index 和 dms_step_index 會形成此視圖的索引鍵。|請參閱[dm_pdw_exec_requests &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)中的 request_id。|  
|step_index|**int**|此 DMS 背景工作角色所屬的查詢步驟。<br /><br /> request_id、step_index 和 dms_step_index 會形成此視圖的索引鍵。|請參閱[dm_pdw_request_steps &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)中的 step_index。|  
|dms_step_index|**int**|此背景工作正在執行之 DMS 計畫中的步驟。<br /><br /> request_id、step_index 和 dms_step_index 會形成此視圖的索引鍵。||  
|pdw_node_id|**int**|正在執行背景工作的節點。|請參閱[dm_pdw_nodes &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)中的 node_id。|  
|distribution_id|**Int**|背景工作執行所在的散發（如果有的話）。|請參閱[pdw_distributions &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md)中的 distribution_id。|  
|type|**Nvarchar （32）**|此專案所代表的 DMS 工作者執行緒類型。|[DIRECT_CONVERTER]、[DIRECT_READER]、[FILE_READER]、[HASH_CONVERTER]、[HASH_READER]、[ROUNDROBIN_CONVERTER]、[EXPORT_READER]、[EXTERNAL_READER]、[EXTERNAL_WRITER]、[PARALLEL_COPY_READER]、[REJECT_WRITER]、[WRITER]|  
|status|**Nvarchar （32）**|DMS 背景工作角色的狀態。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**Bigint**|上一秒的讀取或寫入輸送量。|大於或等於0。 如果在執行背景工作之前，查詢已取消或失敗，則為 Null。|  
|bytes_processed|**Bigint**|此背景工作所處理的位元組總數。|大於或等於0。 如果在執行背景工作之前，查詢已取消或失敗，則為 Null。|  
|rows_processed|**Bigint**|為此背景工作讀取或寫入的資料列數目。|大於或等於0。 如果在執行背景工作之前，查詢已取消或失敗，則為 Null。|  
|start_time|**datetime**|開始執行此工作者的時間。|大於或等於此工作者所屬查詢步驟的開始時間。 請參閱[dm_pdw_request_steps &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|end_time|**datetime**|執行結束、失敗或已取消的時間。|針對進行中或佇列的背景工作角色，則為 Null。 否則，大於 start_time。|  
|total_elapsed_time|**int**|花費在執行的總時間（以毫秒為單位）。|大於或等於0。<br /><br /> 從系統啟動或重新開機以來經過的總時間。 如果 total_elapsed_time 超過整數的最大值（以毫秒為單位的24.8 天），則會造成具體化失敗，因為溢位。<br /><br /> 最大值（以毫秒為單位）相當於24.8 天。|  
|cpu_time|**Bigint**|此工作者耗用的 CPU 時間（以毫秒為單位）。|大於或等於0。|  
|query_time|**int**|SQL 開始將資料列傳回給執行緒之前的時間長度（以毫秒為單位）。|大於或等於0。|  
|buffers_available|**int**|未使用的緩衝區數目。| 如果在執行背景工作之前，查詢已取消或失敗，則為 Null。|  
|sql_spid|**int**|執行此 DMS 工作者工作的 SQL Server 實例上的會話識別碼。||  
|dms_cpid|**int**|實際執行之執行緒的處理序識別碼。||  
|error_id|**Nvarchar （36）**|執行此背景工作時所發生之錯誤的唯一識別碼（如果有的話）。|請參閱[dm_pdw_request_steps &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)中的 error_id。|  
|source_info|**nvarchar(4000)**|若為讀取器，則為來源資料表和資料行的規格。||  
|destination_info|**nvarchar(4000)**|針對寫入器，這是目的地資料表的規格。||  
  
 如需此視圖所保留之最大資料列的詳細資訊，請參閱[容量限制](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)主題中的 Metadata 一節。  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理 Views &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
