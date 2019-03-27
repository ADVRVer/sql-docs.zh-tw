---
title: sp_changelogreader_agent & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changelogreader_agent
- sp_changelogreader_agent_TSQL
helpviewer_keywords:
- sp_changelogreader_agent
ms.assetid: 929b2fa7-1267-41d0-8b69-e9ab26a62c0f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6d3671c96b73fa1fb8138a7085748704c7a38d76
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494220"
---
# <a name="spchangelogreaderagent-transact-sql"></a>sp_changelogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  變更記錄讀取器代理程式的安全性屬性。 這個預存程序執行於發行集資料庫的發行者端。  
  
> [!IMPORTANT]  
>  當利用遠端散發者來設定發行者時，提供給所有參數的值 (包括 *job_login* 和 *job_password*) 都會以純文字的方式傳給散發者。 您應該先加密「發行者」及其遠端「散發者」之間的連接，再執行這個預存程序。 如需詳細資訊，請參閱[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_changelogreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @job_login = ] 'job_login'` 是執行代理程式帳戶的登入。 *job_login*已**nvarchar(257)**，預設值是 NULL。 Azure SQL Database 受控執行個體，使用 SQL Server 帳戶。 *無法變更為非*[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *發行者。*  
  
`[ @job_password = ] 'job_password'` 是執行代理程式帳戶的密碼。 *job_password*已**sysname**，預設值是 NULL。  
  
> [!IMPORTANT]  
>  可能的話，會在執行階段提示使用者輸入安全性認證。 如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。  
  
`[ @publisher_security_mode = ] publisher_security_mode` 是的安全性模式，代理程式用來連接到發行者。 *publisher_security_mode*已**smallint**，預設值是 NULL。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證，並**1**指定 Windows 驗證。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` 已連接到發行者時使用的登入。 *publisher_login*已**sysname**，預設值是 NULL。 *publisher_login*時，必須指定*publisher_security_mode*是**0**。 如果*publisher_login*為 NULL 並*publisher_security_mode*是**1**，在指定的 Windows 帳戶*job_login*時使用連接到發行者。  
  
`[ @publisher_password = ] 'publisher_password'` 這是連接到 「 發行者 」 時用的密碼。 *publisher_password*已**sysname**，預設值是 NULL。  
  
> [!IMPORTANT]  
>  請勿使用空白密碼。 請使用增強式密碼。 可能的話，會在執行階段提示使用者輸入安全性認證。 如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。  
  
`[ @publisher = ] 'publisher'` 是 「 發行者 」 的名稱。 *發行者*已**sysname**，預設值是 NULL。 只支援非 SQL Server 發行者使用這個參數。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_changelogreader_agent**用於異動複寫中。  
  
 **sp_changelogreader_agent**用來變更記錄讀取器代理程式所執行的 Windows 帳戶。 您可以變更現有 Windows 登入的密碼，或者提供新的 Windows 登入和密碼。  
  
 變更代理程式的登入或密碼之後，您必須先停止並重新啟動代理程式，變更才會生效。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_changelogreader_agent**。  
  
## <a name="see-also"></a>另請參閱  
 [檢視及修改複寫安全性設定](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_helplogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md)   
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  
