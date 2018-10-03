---
title: sp_delete_operator (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_operator
- sp_delete_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_operator
ms.assetid: ff6c2c4b-e9fe-4d0c-bbc2-a2ddcc1acb95
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2b55d44a837cc721761ebe77352962d1dea88f55
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704656"
---
# <a name="spdeleteoperator-transact-sql"></a>sp_delete_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  移除操作員。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_delete_operator [ @name = ] 'name'   
     [ , [ @reassign_to_operator = ] 'reassign_operator' ]   
```  
  
## <a name="arguments"></a>引數  
 [ **@name=** ] **'***name***'**  
 要刪除的操作員名稱。 *名稱*已**sysname**，沒有預設值。  
  
 [ **@reassign_to_operator=** ]  **'***reassign_operator***'**  
 能夠重新指派指定操作員的警示之操作員名稱。 *reassign_operator*已**sysname**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 當移除操作員時，也會移除操作員的所有相關通知。  
  
## <a name="permissions"></a>Permissions  
 成員**sysadmin**固定的伺服器角色可以執行**sp_delete_operator**。  
  
## <a name="examples"></a>範例  
 下列範例會刪除 `François Ajenstat` 這位操作員。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_operator @name = 'François Ajenstat' ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_operator &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
