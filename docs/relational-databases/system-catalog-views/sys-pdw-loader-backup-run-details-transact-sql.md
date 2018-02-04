---
title: "sys.pdw_loader_backup_run_details (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02b934db7152723e66aab5818751cb748d2e2a87
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  包含進一步的詳細的資訊中的資訊以外[sys.pdw_loader_backup_runs &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)、 進行中和已完成的備份和還原作業中的相關[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]有關進行中和已完成的備份、 還原及載入作業中的以及[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]。 資訊會保留在系統重新啟動。  
  
|資料行名稱|資料類型|Description|範圍|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|特定的備份或還原執行的唯一識別碼。<br /><br /> run_id 和 pdw_node_id 形成這個檢視的索引鍵。||  
|pdw_node_id|**int**|應用裝置節點，此記錄會保留詳細資料的唯一識別碼。<br /><br /> run_id 和 pdw_node_id 形成這個檢視的索引鍵。|請參閱中的 node_id [sys.dm_pdw_nodes &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16)**|執行目前的狀態。|'取消'，' 填寫 '，'失敗'、 '佇列更新'、 '執行'|  
|start_time|**datetime**|在此特定節點的作業開始的時間。||  
|end_time|**datetime**|結束的時間操作此特定節點上，如果有的話。||  
|total_elapsed_time|**int**|已在此特定節點執行作業的時間總計。|如果 total_elapsed_time 超過整數 （以毫秒為單位的 24.8 天） 的最大值，它會導致具體化失敗，因為發生溢位。<br /><br /> 以毫秒為單位的最大值就相當於 24.8 天。|  
|進度|**int**|以百分比表示該作業的進度。|0 到 100|  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲目錄檢視](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
