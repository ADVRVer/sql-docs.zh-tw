---
title: MSmerge_articlehistory (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_articlehistory
- MSmerge_articlehistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_articlehistory system table
ms.assetid: 2870e7ea-dbec-4636-9171-c2cee96018ac
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b19b67ab4fce3b27ebb46666a3c1705a13ffeff5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="msmergearticlehistory-transact-sql"></a>MSmerge_articlehistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_articlehistory**資料表會追蹤合併代理程式同步處理工作階段，有一個資料列，每個發行項的變更發行項所做的變更。 這份資料表儲存在散發資料庫中。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|中的合併代理程式作業工作階段識別碼[MSmerge_sessions](../../relational-databases/system-tables/msmerge-sessions-transact-sql.md)系統資料表。|  
|**phase_id**|**int**|同步處理工作階段的階段，它可以是下列項目之一：<br /><br /> **1** = 上傳。<br /><br /> **2** = 下載。<br /><br /> **4** = 清除。<br /><br /> **5** = 關機。<br /><br /> **6** = 結構描述變更。<br /><br /> **7** = BCP。|  
|**article_name**|**sysname**|更改過的發行項名稱。|  
|**start_time**|**datetime**|代理程式開始處理發行項的時間。|  
|**duration**|**int**|代理程式處理發行項所花的時間 (以秒計)。|  
|**插入**|**int**|在同步處理時，曾經套用至某篇特定發行項的插入數量。 這個值會在同步處理時增加，而結束值就代表總數。|  
|**更新**|**int**|在同步處理時，曾經套用至某篇特定發行項的更新數量。 這個值會在同步處理時增加，而結束值就代表總數。|  
|**刪除**|**int**|在同步處理時，曾經套用至某篇特定發行項的刪除數量。 這個值會在同步處理時增加，而結束值就代表總數。|  
|**衝突**|**int**|在同步處理時所發生的衝突數量。 這個值會在同步處理時增加，而結束值就代表總數。|  
|**conflicts_resolved**|**int**|在進行已解析的同步處理時所發生的衝突數量。 這個值會在同步處理時增加，而結束值就代表總數。|  
|**rows_retried**|**int**|在同步處理時重試的失敗列數。 這個值會在同步處理時增加，而結束值就代表總數。|  
|**percent_complete**|**decimal**|合併代理程式在工作階段時，花在該發行項的總同步處理時間的百分比。 這個值是 NULL，維持到工作階段完成為止。|  
|**estimated_changes**|**int**|必須套用至發行項的資料列變更數預估值。|  
|**relative_cost**|**decimal**|將變更套用至這個發行項所花的時間，對整個工作階段的總時間比。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
