---
title: "sp_msx_set_account (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_msx_set_account
- sp_msx_set_account_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_msx_set_account
ms.assetid: 314ec720-3a37-48f7-bb6b-8d5b894bf843
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3f1d1cc901c592c716cd2e10e1fe3ac6445efe09
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="spmsxsetaccount-transact-sql"></a>sp_msx_set_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在目標伺服器上，設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 主要伺服器的帳戶名稱和密碼。  
  
||  
|-|  
|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_msx_set_account [ @credential_name = ] 'credential_name'  | [ @credential_id = ] credential_id  
```  
  
## <a name="arguments"></a>引數  
 [  **@credential_name=** ] **'***credential_name***'**  
 用來登入主要伺服器的認證名稱。 提供的名稱必須是現有認證的名稱。 任一*credential_name*或*credential_id*必須指定。  
  
 [  **@credential_id=** ] *credential_id*  
 用來登入主要伺服器的認證識別碼。 識別碼必須是現有認證的識別碼。 任一*credential_name*或*credential_id*必須指定。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 無。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會利用認證來儲存目標伺服器用來登入主要伺服器的使用者名稱和密碼資訊。 這個程序會設定這部目標伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 用來登入主要伺服器的認證。  
  
 指定的認證必須是現有的認證。 如需建立認證的詳細資訊，請參閱[CREATE CREDENTIAL &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 執行權限**sp_msx_set_account**成員的預設權**sysadmin**固定的伺服器角色。  
  
## <a name="examples"></a>範例  
 下列範例會將這部伺服器設定成利用 `MsxAccount` 認證來登入主要伺服器。  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_set_account @credential_name = MsxAccount ;  
GO  
```  
  
## <a name="see-also"></a>請參閱＜  
 [SQL Server Agent 預存程序 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_get_account &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-msx-get-account-transact-sql.md)  
  
  
