---
title: sp_delete_alert （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_alert_TSQL
- sp_delete_alert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_alert
ms.assetid: a831315e-793d-41c4-8333-b324bb2bc614
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5066571ed19984d88d5ef134a778865ff1bfe1a3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750677"
---
# <a name="sp_delete_alert-transact-sql"></a>sp_delete_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  移除警示。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_delete_alert [ @name = ] 'name'  
```  
  
## <a name="arguments"></a>引數  
`[ @name = ] 'name'`警示的名稱。 *名稱*是**sysname**，沒有預設值。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 移除警示也會移除警示的任何相關通知。  
  
## <a name="permissions"></a>權限  
 只有**系統管理員（sysadmin** ）固定伺服器角色的成員，才能夠執行此程式。  
  
## <a name="examples"></a>範例  
 下列範例會移除名稱為 `Test Alert` 的警示。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_alert  
   @name = N'Test Alert' ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_alert &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
