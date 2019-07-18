---
title: sys.dm_pdw_sys_info (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 0bc6c97f4d41023b822f42a6bbe4c5b193d42e45
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088749"
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  提供一組的應用裝置層級的計數器會反映在應用裝置上的整體活動。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|目前在系統中的工作階段數目。|0 表示 max_active_sessions （如下所示）。|  
|idle_sessions|**int**|目前處於閒置狀態的工作階段數目。||  
|active_requests|**int**|目前正在執行的使用中要求數目。||  
|queued_requests|**int**|目前排入佇列的要求數目。||  
|active_loads|**int**|載入目前在系統中執行的數目。||  
|queued_loads|**int**|已排入佇列等候執行的負載數目。||  
|active_backups|**int**|目前正在執行的備份數目。||  
|active_restores|**int**|目前正在執行的備份還原的數目。||  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理檢視&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
