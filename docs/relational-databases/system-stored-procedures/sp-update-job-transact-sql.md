---
description: sp_update_job (Transact-SQL)
title: sp_update_job (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_job
- sp_update_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_job
ms.assetid: cbdfea38-9e42-47f3-8fc8-5978b82e2623
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 494e284bb9df06094116d075979673bf2b033dea
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551181"
---
# <a name="sp_update_job-transact-sql"></a>sp_update_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  變更作業的屬性。  
  

  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_update_job [ @job_id =] job_id | [@job_name =] 'job_name'  
     [, [@new_name =] 'new_name' ]   
     [, [@enabled =] enabled ]  
     [, [@description =] 'description' ]   
     [, [@start_step_id =] step_id ]  
     [, [@category_name =] 'category' ]   
     [, [@owner_login_name =] 'login' ]  
     [, [@notify_level_eventlog =] eventlog_level ]  
     [, [@notify_level_email =] email_level ]  
     [, [@notify_level_netsend =] netsend_level ]  
     [, [@notify_level_page =] page_level ]  
     [, [@notify_email_operator_name =] 'operator_name' ]  
     [, [@notify_netsend_operator_name =] 'netsend_operator' ]  
     [, [@notify_page_operator_name =] 'page_operator' ]  
     [, [@delete_level =] delete_level ]   
     [, [@automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>引數  
`[ @job_id = ] job_id` 要更新之作業的識別碼。 *job_id*為 **uniqueidentifier**。  
  
`[ @job_name = ] 'job_name'` 作業的名稱。 *job_name* 是 **Nvarchar (128) **。  
  
> **注意：** 必須指定 *job_id* 或 *job_name* ，但不能同時指定兩者。  
  
`[ @new_name = ] 'new_name'` 作業的新名稱。 *new_name* 是 **Nvarchar (128) **。  
  
`[ @enabled = ] enabled` 指定 (**1**) 或未啟用 (**0**) 時，是否啟用作業。 *啟用* 是 **Tinyint**。  
  
`[ @description = ] 'description'` 作業的描述。 *描述* 是 **Nvarchar (512) **。  
  
`[ @start_step_id = ] step_id` 要為作業執行之第一個步驟的識別碼。 *step_id* 為 **int**。  
  
`[ @category_name = ] 'category'` 作業的類別目錄。 *類別目錄* 是 **Nvarchar (128) **。  
  
`[ @owner_login_name = ] 'login'` 擁有作業的登入名稱。 *登* 入為 **Nvarchar (128) ** 只有 **系統管理員（sysadmin** ）固定伺服器角色的成員可以變更作業擁有權。  
  
`[ @notify_level_eventlog = ] eventlog_level` 指定何時將專案放在 Microsoft Windows 應用程式記錄檔中，以進行這項作業。 *eventlog_level*是 **int**，而且可以是下列值之一。  
  
|值|描述 (動作)|  
|-----------|----------------------------|  
|**0**|永不|  
|**1**|成功時|  
|**2**|失敗時|  
|**3**|一律|  
  
`[ @notify_level_email = ] email_level` 指定在此作業完成時傳送電子郵件的時機。 *email_level*為 **int**。 *email_level*使用與 *eventlog_level*相同的值。  
  
`[ @notify_level_netsend = ] netsend_level` 指定在此作業完成時傳送網路訊息的時機。 *netsend_level*為 **int**。 *netsend_level*使用與 *eventlog_level*相同的值。  
  
`[ @notify_level_page = ] page_level` 指定在此作業完成時傳送頁面的時機。 *page_level* 為 **int**。 *page_level*使用與 *eventlog_level*相同的值。  
  
`[ @notify_email_operator_name = ] 'operator_name'` 當達到 *email_level* 時，傳送電子郵件的目標操作員名稱。 *email_name* 是 **Nvarchar (128) **。  
  
`[ @notify_netsend_operator_name = ] 'netsend_operator'` 要傳送網路訊息的目標操作員名稱。 *netsend_operator* 是 **Nvarchar (128) **。  
  
`[ @notify_page_operator_name = ] 'page_operator'` 傳送頁面的目標操作員名稱。 *page_operator* 是 **Nvarchar (128) **。  
  
`[ @delete_level = ] delete_level` 指定何時刪除作業。 *delete_value*為 **int**。 *delete_level*使用與 *eventlog_level*相同的值。  
  
`[ @automatic_post = ] automatic_post` 保留。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_update_job** 必須從 **msdb** 資料庫執行。  
  
 **sp_update_job** 只會變更提供參數值的設定。 如果省略某個參數，就會保留目前的設定。  
  
## <a name="permissions"></a>權限  
 依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。 其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 如需這些角色權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。  
  
 只有 **系統管理員（sysadmin** ）的成員可以使用此預存程式來編輯其他使用者所擁有的作業屬性。  
  
## <a name="examples"></a>範例  
 下列範例會變更 `NightlyBackups` 作業的名稱、描述和啟用狀態。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_job  
    @job_name = N'NightlyBackups',  
    @new_name = N'NightlyBackups -- Disabled',  
    @description = N'Nightly backups disabled during server migration.',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
