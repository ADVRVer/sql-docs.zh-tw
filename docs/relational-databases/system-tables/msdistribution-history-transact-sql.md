---
title: "Y (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdistribution_history
- MSdistribution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_history system table
ms.assetid: 55665bd2-9e1d-4efc-8f60-c63a24f66b28
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa93b984ecd15cc3c0629e0eaaf6310142943dfe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="msdistributionhistory-transact-sql"></a>MSdistribution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistribution_history**資料表包含記錄資料列與本機散發者的散發代理程式相關聯。 這份資料表儲存在散發資料庫中。  
  
## <a name="definition"></a>定義  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|散發代理程式的識別碼。|  
|**runstatus**|**int**|執行狀態：<br /><br /> **1** = 開始。<br /><br /> **2** = 成功。<br /><br /> **3** = 進行中。<br /><br /> **4** = 閒置。<br /><br /> **5** = 重試。<br /><br /> **6** = 失敗。|  
|**start_time**|**datetime**|開始執行作業的時間。|  
|**time**|**datetime**|記錄訊息的時間。|  
|**duration**|**int**|訊息工作階段的持續時間 (以秒為單位)。|  
|**註解**|**nvarchar(4000)**|訊息文字。|  
|**xact_seqno**|**varbinary （16)**|前次處理的交易序號。|  
|**current_delivery_rate**|**float**|在最後一個記錄項目之後，每秒傳遞的平均命令數。|  
|**current_delivery_latency**|**int**|在前一個記錄項目之後，在命令輸入散發資料庫和套用至訂閱者之間的延遲 (毫秒)。|  
|**delivered_transactions**|**int**|在工作階段所傳遞的交易總數。|  
|**delivered_commands**|**int**|在工作階段所傳遞的命令總數。|  
|**average_commands**|**int**|在工作階段所傳遞的命令平均數。|  
|**delivery_rate**|**float**|平均每秒傳遞的命令數。|  
|**delivery_latency**|**int**|在命令輸入散發資料庫和套用至訂閱者之間的延遲 (毫秒)。|  
|**total_delivered_commands**|**bigint**|建立訂閱之後所傳遞的命令總數。|  
|**error_id**|**int**|中的錯誤訊息的識別碼**MSrepl_error**系統資料表。|  
|**updateable_row**|**bit**|設定為**1**如果可以覆寫記錄資料列。|  
|**timestamp**|**timestamp**|這份資料表的時間戳記資料行。|  
  
## <a name="see-also"></a>請參閱＜  
 [複寫資料表 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
