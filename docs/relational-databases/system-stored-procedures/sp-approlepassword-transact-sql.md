---
title: sp_approlepassword （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_approlepassword
- sp_approlepassword_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_approlepassword
ms.assetid: 7967dc0b-bee2-4c63-b8e9-1c3ce2f5db2a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 22d91d3422a9d2c6152d26a82c9e17754d0e21c9
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833522"
---
# <a name="sp_approlepassword-transact-sql"></a>sp_approlepassword (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  變更目前資料庫中應用程式角色的密碼。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]請改用[ALTER APPLICATION ROLE](../../t-sql/statements/alter-application-role-transact-sql.md) 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_approlepassword [ @rolename= ] 'role' , [ @newpwd = ] 'password'   
```  
  
## <a name="arguments"></a>引數  
`[ @rolename = ] 'role'`這是應用程式角色的名稱。 *Role*是**sysname**，沒有預設值。 *角色*必須存在於目前的資料庫中。  
  
`[ @newpwd = ] 'password'`這是應用程式角色的新密碼。 *password*是**sysname**，沒有預設值。 *密碼*不可以是 Null。  
  
> [!IMPORTANT]  
>  請勿使用 NULL 密碼。 請使用增強式密碼。 如需詳細資訊，請參閱 [Strong Passwords](../../relational-databases/security/strong-passwords.md)。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_approlepassword**不能在使用者自訂交易內執行。  
  
## <a name="permissions"></a>權限  
 需要資料庫的 ALTER ANY APPLICATION ROLE 權限。  
  
## <a name="examples"></a>範例  
 下列範例會將 `PayrollAppRole` 應用程式角色的密碼設為 `B3r12-36`。  
  
```  
EXEC sp_approlepassword 'PayrollAppRole', '''B3r12-36';  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的安全性預存程式](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [應用程式角色](../../relational-databases/security/authentication-access/application-roles.md)   
 [sp_addapprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [sp_setapprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
