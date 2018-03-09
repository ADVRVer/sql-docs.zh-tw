---
title: sp_grant_login_to_proxy (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_proxy
- sp_grant_login_to_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_login_to_proxy
ms.assetid: 90e1a6d5-a692-4462-a163-4b0709d83150
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b5a4788da049ef1d3c69f604aacdf9000f9ed624
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="spgrantlogintoproxy-transact-sql"></a>sp_grant_login_to_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  授與 Proxy 的安全性主體存取權。  

  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_grant_login_to_proxy   
     { [ @login_name = ] 'login_name'   
     | [ @fixed_server_role = ] 'fixed_server_role'   
     | [ @msdb_role = ] 'msdb_role' } ,   
     { [ @proxy_id = ] id | [ @proxy_name = ] 'proxy_name' }  
```  
  
## <a name="arguments"></a>引數  
 [ **@login_name** = ] **'***login_name***'**  
 要授與存取權的登入名稱。 *Login_name*是**nvarchar （256)**，預設值是 NULL。 其中一個 **@login_name** ，  **@fixed_server_role** ，或 **@msdb_role** 必須指定，或預存程序會失敗。  
  
 [ **@fixed_server_role**= ] **'***fixed_server_role***'**  
 要授與存取權的固定伺服器角色。 *Fixed_server_role*是**nvarchar （256)**，預設值是 NULL。 其中一個 **@login_name** ，  **@fixed_server_role** ，或 **@msdb_role** 必須指定，或預存程序會失敗。  
  
 [ **@msdb_role**= ] '*msdb_role*'  
 中的資料庫角色**msdb**授與存取權的資料庫。 *Msdb_role*是**nvarchar （256)**，預設值是 NULL。 其中一個 **@login_name** ，  **@fixed_server_role** ，或 **@msdb_role** 必須指定，或預存程序會失敗。  
  
 [ **@proxy_id**= ] *id*  
 要授與存取權的 Proxy 識別碼。 *識別碼*是**int**，預設值是 NULL。 其中一個 **@proxy_id** 或 **@proxy_name** 必須指定，或預存程序會失敗。  
  
 [ **@proxy_name**= ] **'***proxy_name***'**  
 要授與存取權的 Proxy 名稱。 *Proxy_name*是**nvarchar （256)**，預設值是 NULL。 其中一個 **@proxy_id** 或 **@proxy_name** 必須指定，或預存程序會失敗。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_grant_login_to_proxy**必須從執行**msdb**資料庫。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色可能會執行**sp_grant_login_to_proxy**。  
  
## <a name="examples"></a>範例  
 下列範例可讓登入`adventure-works\terrid`使用 proxy `Catalog application proxy`。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_login_to_proxy  
    @login_name = N'adventure-works\terrid',  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
