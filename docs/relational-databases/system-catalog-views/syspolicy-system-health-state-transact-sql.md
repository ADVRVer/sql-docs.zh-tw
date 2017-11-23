---
title: "syspolicy_system_health_state (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs: TSQL
helpviewer_keywords: syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e3aa7ef860f35917adc330b6c8c49b3692b5e6f4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="syspolicysystemhealthstate-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對每一個以原則為基礎的管理原則和目標查詢運算式組合各顯示一個資料列。 使用 syspolicy_system_health_state 檢視表可透過程式設計方式檢查伺服器的原則健全狀態。 下表描述 syspolicy_system_health_state 檢視表中的資料行。  
  
||  
|-|  
|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|health_state_id|**bigint**|原則健全狀態記錄的識別碼。|  
|policy_id|**int**|原則的識別碼。|  
|last_run_date|**datetime**|上次執行此原則的日期和時間。|  
|target_query_expression_with_id|**nvarchar （400)**|目標運算式 (具有指派給識別變數的值)，可針對評估的原則定義目標。|  
|target_query_expression|**nvarchar(max)**|運算式，可針對評估的原則定義目標。|  
|result|**bit**|這個目標與此原則有關的健全狀態：<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
  
## <a name="remarks"></a>備註  
 syspolicy_system_health_state 檢視表會顯示每一個使用中 (已啟用) 原則之目標查詢運算式的最近健全狀態。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [物件總管] 和 [物件總管詳細資料] 頁面會從這個檢視表彙總原則健全狀態，以顯示關鍵健全狀態。  
  
## <a name="permissions"></a>Permissions  
 需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。  
  
## <a name="see-also"></a>請參閱＜  
 [使用原則式管理來管理伺服器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [以原則為基礎的管理檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
