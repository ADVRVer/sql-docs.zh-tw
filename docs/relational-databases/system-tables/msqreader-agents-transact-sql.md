---
title: MSqreader_agents (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSqreader_agents_TSQL
- MSqreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSqreader_agents system table
ms.assetid: dfa1f45e-c531-4385-a097-0a9edd1d7eab
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eb1a85b0a1c81b792f14afd428aa5e46c357b62d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842381"
---
# <a name="msqreaderagents-transact-sql"></a>MSqreader_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSqreader_agents**資料表針對本機散發者端執行每個佇列讀取器代理程式包含一個資料列。 這份資料表儲存在散發資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**id**|**int**|佇列讀取器代理程式的識別碼。|  
|**name**|**nvarchar(100)**|佇列讀取器代理程式的名稱。|  
|**job_id**|**binary(16)**|中的唯一工作識別碼編號**sysjobs**資料表。|  
|**profile_id**|**int**|從設定檔識別碼**MSagent_profiles**資料表。|  
|**job_step_uid**|**uniqueidentifier**|用來啟動代理程式之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟的唯一識別碼。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
