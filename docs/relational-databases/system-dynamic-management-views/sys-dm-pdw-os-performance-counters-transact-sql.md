---
title: "sys.dm_pdw_os_performance_counters (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b4b346df5211f91519accf3c81374d0ab7302ec
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwosperformancecounters-transact-sql"></a>sys.dm_pdw_os_performance_counters (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  包含有關 Windows 效能計數器中的節點資訊[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]。  
  
|資料行名稱|資料類型|Description|範圍|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|其中包含的計數器節點的識別碼。<br /><br /> pdw_node_id 和 counter_name 形成這個檢視的索引鍵。|請參閱中的 node_id [sys.dm_pdw_nodes &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|counter_name|**nvarchar(255)**|Windows 效能計數器的名稱。||  
|counter_category|**nvarchar(255)**|Windows 效能計數器分類的名稱。||  
|instance_name|**nvarchar(255)**|計數器的特定執行個體名稱。||  
|counter_value|**Decimal(38,10)**|計數器的目前值。||  
|last_update_time|**Datetime2(3)**|上次更新此值的時間戳記。||  
  
## <a name="see-also"></a>請參閱＜  
 [SQL 資料倉儲和平行處理資料倉儲動態管理檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
