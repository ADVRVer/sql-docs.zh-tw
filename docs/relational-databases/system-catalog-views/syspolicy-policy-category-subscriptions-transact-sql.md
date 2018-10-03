---
title: syspolicy_policy_category_subscriptions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_category_subscriptions_TSQL
- syspolicy_policy_category_subscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_group_subscriptions view
ms.assetid: b3b3a7d7-0b78-46c0-9755-045f7a5692b9
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 845b665c108c2d91ef5876667e71a5c883ec8e80
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735009"
---
# <a name="syspolicypolicycategorysubscriptions-transact-sql"></a>syspolicy_policy_category_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中，針對每一個以原則為基礎的管理訂閱各顯示一個資料列。 每個資料列描述目標和原則類別目錄配對。 下表描述 syspolicy_policy_group_subscriptions 檢視表中的資料行。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|policy_category_subscription_id|**int**|這筆記錄的識別碼。|  
|target_type|**sysname**|此描述之目標的資料庫物件類型。|  
|target_object|**sysname**|目標物件的名稱。|  
|policy_category_id|**int**|套用到目標之原則類別目錄的識別碼。|  
  
## <a name="remarks"></a>備註  
 這個檢視表會顯示訂閱原則類別目錄的目標。  
  
## <a name="permissions"></a>Permissions  
 需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來管理伺服器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [以原則為基礎的管理檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
