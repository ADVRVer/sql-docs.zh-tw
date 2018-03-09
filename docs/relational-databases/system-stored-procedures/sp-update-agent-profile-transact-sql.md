---
title: "sp_update_agent_profile (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_update_agent_profile_TSQL
- sp_update_agent_profile
helpviewer_keywords:
- sp_update_agent_profile
ms.assetid: cc81f227-0df3-4151-bb4d-4f45ea997b71
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d4f3088c28098611567b80de916b84b73800dc2e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="spupdateagentprofile-transact-sql"></a>sp_update_agent_profile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  更新複寫代理程式所用的設定檔。 這個預存程序執行於散發資料庫的散發者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_update_agent_profile [@agent_type=] agent_type, [ @agent_id= ] agent_id, [ @profile_id= ] profile_id  
```  
  
## <a name="arguments"></a>引數  
 [**@agent_type=**] **'***agent_type***'**  
 這是代理程式的類型。 *agent_type*是**int**，沒有預設值，它可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|快照集代理程式。|  
|**2**|記錄讀取器代理程式。|  
|**3**|散發代理程式。|  
|**4**|合併代理程式。|  
|**9**|佇列讀取器代理程式。|  
  
 [**@agent_id=**] *agent_id*  
 這是代理程式的識別碼。 *agent_id*是**int**，沒有預設值。  
  
 [**@profile_id=**] *profile_id*  
 這是代理程式應使用的設定檔識別碼。 *profile_id*是**int**，沒有預設值。 若要檢視的定義每個代理程式設定檔清單，請使用[sp_help_agent_profile &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). 如需系統設定檔的詳細資訊，請參閱[Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md)。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_update_agent_profile**用於所有複寫類型。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色可以執行**sp_update_agent_profile**。  
  
## <a name="see-also"></a>請參閱＜  
 [複寫代理程式設定檔](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_profile &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_change_agent_profile &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_drop_agent_profile &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_profile &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
