---
title: sys.databases dm_pdw_query_stats_xe （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d551241-db35-4958-b60f-55e996f95c1f
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 220661cd5573d6160f69130760ef3046c986ae1e
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394850"
---
# <a name="sysdm_pdw_query_stats_xe-transact-sql"></a>sys.databases dm_pdw_query_stats_xe （Transact-sql）
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  這個 DMV 已被取代，將在未來的版本中移除。 在此版本中，它會傳回0個數據列。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|event|**nvarchar(60)**|此視圖的索引鍵。||  
|event_id|**Nvarchar （36）**|||  
|create_time|**datetime**|||  
|session_id|**int**|會話的識別碼。|請參閱[dm_pdw_exec_sessions &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)中的 session_id。|  
|cpu|**int**|||  
|reads|**int**|自事件啟動後的邏輯讀取數。||  
|writes|**int**|自事件啟動後的邏輯寫入數。||  
|sql_text|**nvarchar(4000)**|||  
|client_app_name|**nvarchar(255)**|||  
|tsql_stack|**nvarchar(255)**|||  
|pdw_node_id|**int**|此 Xevent 實例執行所在的節點。|  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理 Views &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
