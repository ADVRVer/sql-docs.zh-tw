---
title: sysreplicationalerts (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/04/2017
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
- sysreplicationalerts_TSQL
- sysreplicationalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysreplicationalerts system table
ms.assetid: 6ed15828-8cca-4cf0-b2ff-1ecd0d8db11a
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0b3cbb8ee462007f59eac4aea41a10e0253651b3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sysreplicationalerts-transact-sql"></a>sysreplicationalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含會造成引發複寫警示之條件的相關資訊。 這份資料表儲存在**msdb**資料庫。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|警示的識別碼。|  
|**status**|**int**|使用者自訂值：<br /><br /> **0** = 未服務。<br /><br /> **1** = 服務。|  
|**agent_type**|**int**|代理程式的類型：<br /><br /> **1** = 快照集代理程式。<br /><br /> **2** = 記錄讀取器代理程式。<br /><br /> **3** = 散發代理程式。<br /><br /> **4** = 合併代理程式。|  
|**agent_id**|**int**|從資料表的代理程式識別碼**MSsnapshot_agents**， **MSlogreader_agents**， **MSdistribution_agents**，或**MSmerge_agents**。|  
|**error_id**|**int**|儲存在錯誤的識別碼**MSrepl_errors**。|  
|**alert_error_code**|**int**|當記載這項記錄時，所引發之警示的訊息識別碼。|  
|**time**|**datetime**|插入記錄的時間。|  
|**發行者**|**sysname**|與引發這項警示之代理程式相關聯的發行者名稱。|  
|**publisher_db**|**sysname**|與引發這項警示之代理程式相關聯的發行者資料庫。|  
|**發行集**|**sysname**|與引發這項警示之代理程式相關聯的發行集。|  
|**publication_type**|**int**|發行集類型：<br /><br /> **0** = 快照集。<br /><br /> **1** = 交易式。<br /><br /> **2** = 合併式。|  
|**訂閱者**|**sysname**|與引發這項警示之代理程式相關聯的訂閱者名稱。|  
|**subscriber_db**|**sysname**|與引發這項警示之代理程式相關聯的訂閱者資料庫名稱。|  
|**article**|**sysname**|與引發這項警示之代理程式相關聯的發行項名稱。|  
|**destination_object**|**sysname**|與警示相關聯的訂閱資料表名稱。|  
|**source_object**|**sysname**|與警示相關聯的已發行資料表名稱。|  
|**alert_error_text**|**ntext**|警示的文字。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
