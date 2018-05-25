---
title: sys.dm_pdw_dms_external_work (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 47345015-f861-451e-97c4-6e1cb81d1922
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d980034474bc08e57044ecdcf555877b50a0c1f2
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmpdwdmsexternalwork-transact-sql"></a>sys.dm_pdw_dms_external_work (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 保留所有外部作業的資料移動服務 (DMS) 步驟的相關資訊的系統檢視表。  
  
|資料行名稱|資料類型|Description|範圍|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|使用此 DMS 背景工作的查詢。<br /><br /> request_id、 step_index 和 dms_step_index 形成這個檢視的索引鍵。|與中的 request_id 相同[sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)。|  
|step_index|**int**|查詢叫用這個 DMS 背景工作的步驟。<br /><br /> request_id、 step_index 和 dms_step_index 形成這個檢視的索引鍵。|與中 step_index 相同[sys.dm_pdw_request_steps &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|dms_step_index|**int**|目前 DMS 計劃中的步驟。<br /><br /> request_id、 step_index 和 dms_step_index 形成這個檢視的索引鍵。|與中 dms___step_index 相同[sys.dm_pdw_dms_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md)。|  
|pdw_node_id|**int**|正在執行 DMS 背景工作的節點。|與中的 node_id 相同[sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)。|  
|型別|**nvarchar(60)**|此節點正在執行的外部作業的類型。<br /><br /> 檔案分割為已分割成多個較小便在 2008 年的外部 Hadoop 檔案上的作業。|' 檔案分割 '|  
|work_id|**int**|檔案分割識別碼。|大於或等於 0。<br /><br /> 每個計算節點是唯一的。|  
|input_name|**nvarchar(60)**|正在讀取的輸入名稱的字串。|Hadoop 檔案，這是 Hadoop 檔案名稱。|  
|read_location|**bigint**|讀取位置的位移。||  
|estimated_bytes_processed|**bigint**|這個工作者所處理的位元組數目。|大於或等於 0。|  
|長度|**bigint**|檔案分割中的位元組數目。<br /><br /> Hadoop，這對於 HDFS 區塊的大小。|使用者定義。 預設值是 64 MB。|  
|status|**nvarchar(32)**|背景工作的狀態。|暫止，處理、 完成、 失敗、 已中止|  
|start_time|**datetime**|此工作者執行的開始時間。|大於或等於此背景工作所屬的查詢步驟的開始時間。 請參閱[sys.dm_pdw_request_steps &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|end_time|**datetime**|在執行結束、 失敗或已取消的時間。|進行中或已佇列的背景工作為 NULL。 否則，大於 start_time。|  
|total_elapsed_time|**int**|花在執行中，以毫秒為單位的時間總計。|大於或等於 0。<br /><br /> 如果 total_elapsed_time 超過整數的最大值，total_elapsed_time 仍的最大值。 這種情況會產生警告的 「 已超過最大值 」。<br /><br /> 以毫秒為單位的最大值就相當於 24.8 天。|  
  
 這份檢視所保留的最大資料列的相關資訊，請參閱[系統檢視的最大值](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9)。  
  
## <a name="see-also"></a>另請參閱  
 [系統檢視表&#40;Transact SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
