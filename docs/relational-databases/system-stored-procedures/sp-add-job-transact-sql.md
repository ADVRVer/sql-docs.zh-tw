---
title: sp_add_job (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_job_TSQL
- sp_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_job
ms.assetid: 6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9335f011aa823c262bc6bf1fcac383cf868bc418
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43034989"
---
# <a name="spaddjob-transact-sql"></a>sp_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  加入 SQLServerAgent 服務所執行的新作業。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_add_job [ @job_name = ] 'job_name'  
     [ , [ @enabled = ] enabled ]   
     [ , [ @description = ] 'description' ]   
     [ , [ @start_step_id = ] step_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @category_id = ] category_id ]   
     [ , [ @owner_login_name = ] 'login' ]   
     [ , [ @notify_level_eventlog = ] eventlog_level ]   
     [ , [ @notify_level_email = ] email_level ]   
     [ , [ @notify_level_netsend = ] netsend_level ]   
     [ , [ @notify_level_page = ] page_level ]   
     [ , [ @notify_email_operator_name = ] 'email_name' ]   
          [ , [ @notify_netsend_operator_name = ] 'netsend_name' ]   
     [ , [ @notify_page_operator_name = ] 'page_name' ]   
     [ , [ @delete_level = ] delete_level ]   
     [ , [ @job_id = ] job_id OUTPUT ]   
```  
  
## <a name="arguments"></a>引數  
 [ **@job_name =** ] **'***job_name***'**  
 作業的名稱。 名稱必須是唯一的而且不能包含百分比 (**%**) 字元。 *job_name*已 **& lt;languagekeyword>nvarchar(128)</languagekeyword>**，沒有預設值。  
  
 [  **@enabled =** ]*啟用*  
 指出所加入作業的狀態。 *已啟用*已**tinyint**，預設值是 1 （已啟用）。 如果**0**，作業不會啟用，且不會執行根據其排程; 不過，它可以手動執行。  
  
 [ **@description =** ] **'***description***'**  
 這是作業的描述。 *描述*已**nvarchar(512)**，預設值是 NULL。 如果*描述*已省略，會使用 「 沒有可用的說明 」。  
  
 [ **@start_step_id =** ] *step_id*  
 作業所要執行之第一個步驟的識別碼。 *step_id*已**int**，預設值是 1。  
  
 [ **@category_name =** ] **'***category***'**  
 作業的類別目錄。 *類別目錄*已**sysname**，預設值是 NULL。  
  
 [ **@category_id =** ] *category_id*  
 用來指定作業類別目錄的不限特定語言機制。 *category_id*已**int**，預設值是 NULL。  
  
 [ **@owner_login_name =** ] **'***login***'**  
 擁有作業的登入名稱。 *登入*已**sysname**，預設值是 NULL，它解譯為目前的登入名稱。 只有成員**sysadmin**固定的伺服器角色可以設定或變更的值**@owner_login_name**。 如果使用者不是成員的**sysadmin**角色設定，或變更的值**@owner_login_name**，此預存程序的執行會失敗，且會傳回錯誤。  
  
 [ **@notify_level_eventlog =** ] *eventlog_level*  
 這個值表示針對這項作業，何時將項目放在 Microsoft Windows 應用程式記錄中。 *eventlog_level*已**int**，而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**0**|永不|  
|**1**|成功時|  
|**2** (預設值)|失敗時|  
|**3**|永遠|  
  
 [ **@notify_level_email =** ] *email_level*  
 這個值表示在這項作業完成時，何時傳送電子郵件。 *email_level*已**int**，預設值是**0**，表示永不。 *email_level*會使用相同的值*eventlog_level*。  
  
 [ **@notify_level_netsend =** ] *netsend_level*  
 這個值表示在這項作業完成時，何時傳送網路訊息。 *netsend_level*已**int**，預設值是**0**，表示永不。 *netsend_level*會使用相同的值*eventlog_level*。  
  
 [ **@notify_level_page =** ] *page_level*  
 這個值表示在這項作業完成時，何時傳送頁面。 *page_level*已**int**，預設值是**0**，表示永不。 *page_level*會使用相同的值*eventlog_level*。  
  
 [ **@notify_email_operator_name =** ] **'***email_name***'**  
 要傳送電子郵件時的人員的電子郵件名稱*email_level*為止。 *email_name*已**sysname**，預設值是 NULL。  
  
 [ **@notify_netsend_operator_name =** ] **'***netsend_name***'**  
 這項作業完成時，網路訊息所要傳送的操作員名稱。 *netsend_name*已**sysname**，預設值是 NULL。  
  
 [ **@notify_page_operator_name =** ] **'***page_name***'**  
 這項作業完成時，所要呼叫的人員名稱。 *page_name*已**sysname**，預設值是 NULL。  
  
 [ **@delete_level =** ] *delete_level*  
 這是指出何時要刪除作業的值。 *delete_value*已**int**，預設值是 0，表示永不刪除。 *delete_level*會使用相同的值*eventlog_level*。  
  
> [!NOTE]  
>  當*delete_level*是**3**一次執行作業，不論任何排程定義的作業。 此外，如果作業刪除作業本身，也會同時刪除作業的所有記錄。  
  
 [ **@job_id =** ] *job_id***OUTPUT**  
 作業建立成功時，指派給作業的作業識別碼。 *job_id*是 output 變數型別的**uniqueidentifier**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 **@originating_server** 存在於**sp_add_job，** 但並未列在引數。 **@originating_server** 是保留供內部使用。  
  
 在後**sp_add_job**來加入作業，執行**sp_add_jobstep**可用來新增執行活動的工作的步驟。 **sp_add_jobschedule**可以用來建立排程[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理程式服務用來執行作業。 使用**sp_add_jobserver**來設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體執行作業，以及**sp_delete_jobserver**若要移除的作業[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。  
  
 如果作業將會執行在多伺服器環境中的一或多個目標伺服器上，使用**sp_apply_job_to_targets**設定目標伺服器或目標伺服器群組的作業。 若要移除目標伺服器或目標伺服器群組的作業，請使用**sp_remove_job_from_targets**。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供了一種簡單的圖形方式供您管理各項作業，建議您利用這個方式來建立和管理作業基礎結構。  
  
## <a name="permissions"></a>Permissions  
 若要執行這個預存程序，使用者必須隸屬**sysadmin**固定伺服器角色，或被授與下列其中一種[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent 固定資料庫角色，位於**msdb**資料庫：  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 如需有關與每一種固定相關聯的特定權限資訊中，資料庫角色，請參閱 < [SQL Server Agent 固定資料庫角色](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。  
  
 只有成員**sysadmin**固定的伺服器角色可以設定或變更的值**@owner_login_name**。 如果使用者不是成員的**sysadmin**角色設定，或變更的值**@owner_login_name**，此預存程序的執行會失敗，且會傳回錯誤。  
  
## <a name="examples"></a>範例  
  
### <a name="a-adding-a-job"></a>A. 加入作業  
 這個範例會加入名稱為 `NightlyBackups` 的新作業。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-adding-a-job-with-pager-e-mail-and-net-send-information"></a>B. 利用呼叫器、電子郵件和 net send 資訊來加入作業  
 這個範例會建立一項名稱為 `Ad hoc Sales Data Backup` 的作業，以便在作業失敗時通知 `François Ajenstat` (利用呼叫器、電子郵件或網路快顯訊息)，以及在順利完成刪除作業。  
  
> [!NOTE]  
>  這個範例假設名稱為 `François Ajenstat` 的操作員及名稱為 `françoisa` 的登入已經存在。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'Ad hoc Sales Data Backup',   
    @enabled = 1,  
    @description = N'Ad hoc backup of sales data',  
    @owner_login_name = N'françoisa',  
    @notify_level_eventlog = 2,  
    @notify_level_email = 2,  
    @notify_level_netsend = 2,  
    @notify_level_page = 2,  
    @notify_email_operator_name = N'François Ajenstat',  
    @notify_netsend_operator_name = N'François Ajenstat',   
    @notify_page_operator_name = N'François Ajenstat',  
    @delete_level = 1 ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_schedule &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobstep &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_apply_job_to_targets &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_job &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [sp_help_job &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobstep &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_update_job &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
