---
title: sp_manage_jobs_by_login (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_manage_jobs_by_login
- sp_manage_jobs_by_login_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_manage_jobs_by_login
ms.assetid: 832ec15a-6e92-4eb5-8c4a-af4dba79fbaa
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0cd3573c108cdd5a57bbb2cf6d542415710f24c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62957150"
---
# <a name="spmanagejobsbylogin-transact-sql"></a>sp_manage_jobs_by_login (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  刪除或重新指派屬於指定登入的作業。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_manage_jobs_by_login  
     [ @action = ] 'action'  
     [, [@current_owner_login_name = ] 'current_owner_login_name']  
     [, [@new_owner_login_name = ] 'new_owner_login_name']  
```  
  
## <a name="arguments"></a>引數  
`[ @action = ] 'action'` 要針對指定的登入所採取的動作。 *動作*已**varchar(10)** ，沒有預設值。 當*動作*是**刪除**， **sp_manage_jobs_by_login**所擁有的所有作業會都刪除*current_owner_login_name*。 當*動作*是**重新指派**，所有作業都會都指派給*new_owner_login_name*。  
  
`[ @current_owner_login_name = ] 'current_owner_login_name'` 目前作業擁有者的登入名稱。 *current_owner_login_name*已**sysname**，沒有預設值。  
  
`[ @new_owner_login_name = ] 'new_owner_login_name'` 新的作業擁有者的登入名稱。 使用此參數才*動作*是**重新指派**。 *new_owner_login_name*已**sysname**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="permissions"></a>Permissions  
 若要執行這個預存程序，使用者必須授與**sysadmin**固定的伺服器角色。  
  
## <a name="examples"></a>範例  
 下列範例會將 `danw` 的所有作業重新指派給 `françoisa`。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_manage_jobs_by_login  
    @action = N'REASSIGN',  
    @current_owner_login_name = N'danw',  
    @new_owner_login_name = N'françoisa' ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
