---
title: MSqreader_history (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSqreader_history
- MSqreader_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSqreader_history system table
ms.assetid: c5c91d39-513c-4a77-870b-c8ef74a1cd6b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a1d179cbef19e652472714b8010edcaeb12ebcc6
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52779690"
---
# <a name="msqreaderhistory-transact-sql"></a>MSqreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSqreader_history**資料表包含記錄資料列與本機散發者相關聯的佇列讀取器代理程式。 這份資料表儲存在散發資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|佇列讀取器代理程式的識別碼。|  
|**publication_id**|**int**|發行集的識別碼。|  
|**runstatus**|**int**|代理程式的執行狀態：<br /><br /> **1** = 開始時間。<br /><br /> **2** = 成功。<br /><br /> **3** = 進行中。<br /><br /> **4** = 閒置。<br /><br /> **5** = 重試。<br /><br /> **6** = 失敗。|  
|**start_time**|**datetime**|代理程式工作階段啟動的日期和時間。|  
|**time**|**datetime**|上次記錄之訊息的日期和時間。|  
|**duration**|**int**|所記錄之工作階段活動的經歷時間 (以秒為單位)。|  
|**註解**|**nvarchar(255)**|描述性文字。|  
|**transaction_id**|**nvarchar(40)**|與訊息一起儲存的交易識別碼 (如果適用的話)。|  
|**transaction_status**|**int**|交易的狀態。|  
|**transactions_processed**|**int**|在工作階段所處理的累計交易數。|  
|**commands_processed**|**int**|在工作階段所處理的累計命令數。|  
|**delivery_rate**|**float(53)**|每秒傳遞的平均命令數。|  
|**transaction_rate**|**float(53)**|交易處理率。|  
|**訂閱者**|**sysname**|訂閱者的名稱。|  
|**subscriberdb**|**sysname**|訂閱資料庫的名稱。|  
|**error_id**|**int**|如果不是零，則這個數字代表[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]錯誤訊息。|  
|**timestamp**|**timestamp**|資料表的時間戳記資料行。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
