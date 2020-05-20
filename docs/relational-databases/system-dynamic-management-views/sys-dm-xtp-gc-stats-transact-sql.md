---
title: sys.databases dm_xtp_gc_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_gc_stats
- dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_gc_stats dynamic management view
ms.assetid: 8287d611-50e3-43e1-ba8d-3e3793d3ba0e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2e9e9502dda9eab45c27065c37b31109c99c4c4f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829010"
---
# <a name="sysdm_xtp_gc_stats-transact-sql"></a>sys.dm_xtp_gc_stats (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  提供 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 記憶體回收處理序目前行為的相關資訊 (整體統計資料)。  
  
 資料列會在一般交易處理過程中進行記憶體回收，或是由主要記憶體回收執行緒回收，這稱為閒置工作者。 當使用者交易認可時，它會從垃圾收集佇列中清除一個工作專案（[dm_xtp_gc_queue_stats sys.databases &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md)）。 可以進行記憶體回收但是無法由主要使用者交易存取的任何資料列都會由閒置工作者在塵封角落掃描 (掃描不常存取之索引的區域) 時進行記憶體回收。  
  
 如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
  
|資料行名稱|類型|描述|  
|-----------------|----------|-----------------|  
|rows_examined|**bigint**|自從伺服器啟動之後記憶體回收子系統所檢查的資料列數。|  
|rows_no_sweep_needed|**bigint**|沒有塵封角落掃描的情況下移除的資料列數。|  
|rows_first_in_bucket|**bigint**|記憶體回收所檢查的資料列數，這些資料列為雜湊值區中的第一個資料列。|  
|rows_first_in_bucket_removed|**bigint**|記憶體回收所檢查的資料列數，這些資料列為雜湊值區中已移除的第一個資料列。|  
|rows_marked_for_unlink|**bigint**|記憶體回收所檢查的資料列數，這些資料列在其索引中已標示為未連結，且參考計數 =0。|  
|parallel_assist_count|**bigint**|由使用者交易處理的資料列數。|  
|idle_worker_count|**bigint**|閒置工作者所處理的廢棄資料列數目。|  
|sweep_scans_started|**bigint**|記憶體回收子系統所執行的塵封角落掃描次數。|  
|sweep_scans_retries|**bigint**|記憶體回收子系統所執行的塵封角落掃描次數。|  
|sweep_rows_touched|**bigint**|塵封角落處理所讀取的資料列。|  
|sweep_rows_expiring|**bigint**|塵封角落處理所讀取的過期資料列。|  
|sweep_rows_expired|**bigint**|塵封角落處理所讀取的已過期資料列。|  
|sweep_rows_expired_removed|**bigint**|塵封角落處理所移除的已過期資料列。|  
  
## <a name="permissions"></a>權限  
 需要執行個體上的 VIEW SERVER STATE 權限。  
  
## <a name="usage-scenario"></a>使用案例  
 下面是範例輸出：  
  
```  
rows_examined        rows_no_sweep_needed rows_first_in_bucket rows_first_in_bucket_removed  
280085               209512               69905  
rows_first_in_bucket_removed rows_marked_for_unlink parallel_assist_count idle_worker_count  
69905                        0                      8953  
  
idle_worker_count    sweep_scans_started  sweep_scan_retries   sweep_rows_touched  
10306473             670                  0                    1343  
  
sweep_rows_expiring  sweep_rows_expired   sweep_rows_expired_removed  
               0                 673673  
```  
  
## <a name="see-also"></a>另請參閱  
 [記憶體最佳化的資料表動態管理檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
