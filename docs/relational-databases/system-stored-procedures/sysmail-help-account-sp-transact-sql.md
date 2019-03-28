---
title: sysmail_help_account_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_account_sp_TSQL
- sysmail_help_account_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_account_sp
ms.assetid: 87c7c39c-8e05-4e68-9272-45f908809c3b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2dd164f25848d4c6b4f913ca2ddc746d7801fb78
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536610"
---
# <a name="sysmailhelpaccountsp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出 Database Mail 帳戶的相關資訊 (密碼除外)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @account_id = ] account_id` 要列出資訊之帳戶的帳戶識別碼。 *account_id*已**int**，預設值是 NULL。  
  
`[ @account_name = ] 'account_name'` 要列出資訊之帳戶的名稱。 *account_name*已**sysname**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 傳回包含下列資料行的結果集。  
  
||||  
|-|-|-|  
|資料行名稱|資料類型|描述|  
|**account_id**|**int**|帳戶的識別碼。|  
|**name**|**sysname**|帳戶的名稱。|  
|**description**|**nvarchar(256)**|帳戶的描述。|  
|**email_address**|**nvarchar(128)**|傳送訊息的來源電子郵件地址。|  
|**display_name**|**nvarchar(128)**|帳戶的顯示名稱。|  
|**replyto_address**|**nvarchar(128)**|這個帳戶發出的訊息之回應所要送往的地址。|  
|**servertype**|**sysname**|帳戶的電子郵件伺服器類型。|  
|**servername**|**sysname**|帳戶的電子郵件伺服器名稱。|  
|**port**|**int**|電子郵件伺服器所用的通訊埠編號。|  
|**username**|**nvarchar(128)**|如果電子郵件伺服器使用驗證的話，用來登入電子郵件伺服器的使用者名稱。 當**username**是 NULL 時，Database Mail 不使用此帳戶的驗證。|  
|**use_default_credentials**|**bit**|指定是否要使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的認證將郵件傳送至 SMTP 伺服器。 **use_default_credentials** bit，沒有預設值。 當此參數是 1 時，Database Mail 會使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服務的認證。 此參數為 0 時，會使用 Database Mail **@username**並**@password** SMTP 伺服器上進行驗證。 如果**@username**並**@password**是 NULL，則 Database Mail 會使用匿名驗證。 在指定此參數之前，請洽詢 SMTP 管理員。|  
|**enable_ssl**|**bit**|指定 Database Mail 是否使用安全通訊端層 (SSL) 加密通訊。 如果 SMTP 伺服器上需要 SSL，則使用此選項。 **enable_ssl** bit，沒有預設值。 1 表示 Database Mail 會使用 SSL 加密通訊。 0 表示 Database Mail 傳送郵件時不使用 SSL 加密。|  
  
## <a name="remarks"></a>備註  
 若未*account_id*或是*account_name*提供，則**sysmail_help_account**列出所有 Microsoft SQL Server 執行個體中的 Database Mail 帳戶的資訊。  
  
 預存程序**sysmail_help_account_sp**處於**msdb**資料庫中，擁有者**dbo**結構描述。 此程序必須利用三部分名稱來執行，如果目前的資料庫不是**msdb**。  
  
## <a name="permissions"></a>Permissions  
 執行此程序預設值，成員的權限**sysadmin**固定的伺服器角色。  
  
## <a name="examples"></a>範例  
 **A.列出所有帳戶的資訊**  
  
 下列範例會顯示如何列出執行個體中之所有帳戶的帳戶資訊。  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp ;  
```  
  
 範例結果集如下 (行的長度經過編輯)：  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- --------------------------------------- ------------------------- -------------------------------- --------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
149         Audit Account                Account for audit e-mail.               audit@Adventure-Works.com Automated Mailer (Audit)         NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
```  
  
 **B.列出特定帳戶的資訊**  
  
 下列範例會顯示如何列出名稱為 `AdventureWorks Administrator` 之帳戶的帳戶資訊。  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
 範例結果集如下 (行的長度經過編輯)：  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- ------------------------------------------------------ ------------------------- ---------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL     0                       0       
```  
  
## <a name="see-also"></a>另請參閱  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [建立 Database Mail 帳戶](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail 預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
