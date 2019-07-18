---
title: sp_notify_operator & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_notify_operator_TSQL
- sp_notify_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_notify_operator
ms.assetid: c440f5c9-9884-4196-b07c-55d87afb17c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 74558320df59414a756e1655bb073e9bf0d7d73c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107984"
---
# <a name="spnotifyoperator-transact-sql"></a>sp_notify_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  利用 Database Mail 將電子郵件訊息傳送給操作員。  
  
 
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_notify_operator  
    [ @profile_name = ] 'profilename' ,  
    [ @id = ] id ,  
    [ @name = ] 'name' ,  
    [ @subject = ] 'subject' ,  
    [ @body = ] 'message' ,  
    [ @file_attachments = ] 'attachment'  
    [ @mail_database = ] 'mail_host_database'  
```  
  
## <a name="arguments"></a>引數  
`[ @profile_name = ] 'profilename'` 用來傳送訊息的 Database Mail 設定檔的名稱。 *profilename*已 **& lt;languagekeyword>nvarchar(128)</languagekeyword>** 。 如果*profilename*未指定，會使用預設 Database Mail 設定檔。  
  
`[ @id = ] id` 若要傳送訊息給操作員識別碼。 *id*已**int**，預設值是 NULL。 其中一個*識別碼*或是*名稱*必須指定。  
  
`[ @name = ] 'name'` 若要傳送訊息給操作員的名稱。 *名稱*已 **& lt;languagekeyword>nvarchar(128)</languagekeyword>** ，預設值是 NULL。 其中一個*識別碼*或是*名稱*必須指定。  
  
> **注意：** 電子郵件地址必須定義運算子，才能接收訊息。  
  
`[ @subject = ] 'subject'` 電子郵件訊息主旨。 *主旨*已**nvarchar(256)** 沒有預設值。  
  
`[ @body = ] 'message'` 電子郵件訊息的本文。 *訊息*已**nvarchar （max)** 沒有預設值。  
  
`[ @file_attachments = ] 'attachment'` 要附加至電子郵件訊息的檔案名稱。 *附件*已**nvarchar(512)** ，沒有預設值。  
  
`[ @mail_database = ] 'mail_host_database'` 指定郵件主機資料庫的名稱。 *mail_host_database*已 **& lt;languagekeyword>nvarchar(128)</languagekeyword>** 。 如果沒有*mail_host_database*指定，則**msdb**預設會使用資料庫。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 將指定的訊息傳送給指定操作員的電子郵件地址。 如果未設定操作員的電子郵件地址，就會傳回錯誤。  
  
 您必須先設定 Database Mail 和郵件主機資料庫，才能將通知傳給操作員。  
  
## <a name="permissions"></a>Permissions  
 依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。 其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 如需這些角色權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。  
  
## <a name="examples"></a>範例  
 下列範例會利用 `François Ajenstat` Database Mail 設定檔，將通知電子郵件傳給 `AdventureWorks Administrator` 操作員。 電子郵件的主旨是 `Test Notification`。 電子郵件訊息包含 "This is a test of notification via e-mail." 這個句子。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_notify_operator  
   @profile_name = N'AdventureWorks Administrator',  
   @name = N'François Ajenstat',  
   @subject = N'Test Notification',  
   @body = N'This is a test of notification via e-mail.' ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Agent 預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
