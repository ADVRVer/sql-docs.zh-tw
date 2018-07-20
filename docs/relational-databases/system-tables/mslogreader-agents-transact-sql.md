---
title: MSlogreader_agents (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- MSlogreader_agents_TSQL
- MSlogreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_agents system table
ms.assetid: 8baa3c5a-cb40-42d0-b966-00e6d55368e8
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1c4f075b71494c311b4ba7572a9615bdbc0a7dfe
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102146"
---
# <a name="mslogreaderagents-transact-sql"></a>MSlogreader_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSlogreader_agents**資料表針對本機散發者端執行每個記錄讀取器代理程式包含一個資料列。 這份資料表儲存在散發資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**id**|**int**|記錄讀取器代理程式的識別碼。|  
|**name**|**nvarchar(100)**|記錄讀取器代理程式的名稱。|  
|**publisher_id**|**smallint**|發行者的識別碼。|  
|**publisher_db**|**sysname**|發行者資料庫的名稱。|  
|**發行集**|**sysname**|發行集的名稱。|  
|**local_job**|**bit**|指出本機散發者是否有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。|  
|**job_id**|**binary(16)**|作業識別碼。|  
|**profile_id**|**int**|設定識別碼，從[MSagent_profiles](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)資料表。|  
|**publisher_security_mode**|**smallint**|連接到發行者時，代理程式所用的安全性模式，它可以是下列項目之一：<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證。<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證。|  
|**publisher_login**|**sysname**|連接到發行者時所用的登入。|  
|**publisher_password**|**nvarchar(524)**|連接到發行者時，所用之密碼的加密值。|  
|**job_step_uid**|**uniqueidentifier**|用來啟動代理程式之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟的唯一識別碼。|  
|**job_login**|**sysname**||  
|**job_password**|**nvarchar(524)**||  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
