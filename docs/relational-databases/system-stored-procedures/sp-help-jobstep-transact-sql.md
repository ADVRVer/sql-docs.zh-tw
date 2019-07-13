---
title: sp_help_jobstep (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobstep_TSQL
- sp_help_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobstep
ms.assetid: 4a13b804-45f2-4f82-987f-42d9a57dd6db
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5faad4f4e0de6f9c56115bff59933360f551ab55
ms.sourcegitcommit: 4181429ada1169871c2f4d73d18d2ba013007501
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2019
ms.locfileid: "67866275"
---
# <a name="sphelpjobstep-transact-sql"></a>sp_help_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務用來執行自動化活動之作業步驟的資訊。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_jobstep { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]   
     [ , [ @step_name = ] 'step_name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>引數  
`[ @job_id = ] 'job_id'` 作業識別碼為其傳回作業資訊。 *job_id*已**uniqueidentifier**，預設值是 NULL。  
  
`[ @job_name = ] 'job_name'` 作業名稱。 *job_name*已**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  任一*job_id*或是*job_name*必須指定，但不可同時指定兩者。  
  
`[ @step_id = ] step_id` 在 作業步驟的識別碼。 如果沒有包含這個識別碼，便會包含作業中的所有步驟。 *step_id*已**int**，預設值是 NULL。  
  
`[ @step_name = ] 'step_name'` 在 作業步驟的名稱。 *step_name*已**sysname**，預設值是 NULL。  
  
`[ @suffix = ] suffix` 旗標，指出是否有附加文字描述**旗標**在輸出中的資料行。 *後置詞*已**位元**，預設值是**0**。 如果*後置詞*是**1**，有附加的描述。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|步驟的唯一識別碼。|  
|**step_name**|**sysname**|作業中的步驟名稱。|  
|**subsystem**|**nvarchar(40)**|在其中執行步驟命令的子系統。|  
|**command**|**nvarchar(max)**|在步驟中執行的命令。|  
|**flags**|**int**|這是一個位元遮罩，用來控制步驟行為的值。|  
|**cmdexec_success_code**|**int**|針對**CmdExec**步驟中，這是成功命令的處理序結束碼。|  
|**on_success_action**|**tinyint**|步驟成功時所採取的動作：<br /><br /> **1** = 結束作業報告成功。<br /><br /> **2** = 結束作業報告失敗。<br /><br /> **3** = 移至下一個步驟。<br /><br /> **4** = 移至步驟。|  
|**on_success_step_id**|**int**|如果**on_success_action**是 4，這表示要執行的下一個步驟。|  
|**on_fail_action**|**tinyint**|作業失敗時要執行什麼動作。 值會與相同**on_success_action**。|  
|**on_fail_step_id**|**int**|如果**on_fail_action**是 4，這表示要執行的下一個步驟。|  
|**伺服器**|**sysname**|已保留。|  
|**database_name**|**sysname**|如果是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 步驟，這就是命令執行所在的資料庫。|  
|**database_user_name**|**sysname**|如果是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 步驟，這就是命令執行所在的資料庫使用者環境。|  
|**retry_attempts**|**int**|命令應該重試的最大次數 (如果沒有成功)。|  
|**retry_interval**|**int**|任何重試的間隔 (以分鐘為單位)。|  
|**os_run_priority**|**int**|已保留。|  
|**output_file_name**|**nvarchar(200)**|命令輸出應該寫入的檔案 ([!INCLUDE[tsql](../../includes/tsql-md.md)]， **CmdExec**，以及**PowerShell**只有步驟)。|  
|**last_run_outcome**|**int**|上次執行步驟的結果：<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **2** = 重試<br /><br /> **3** = 取消<br /><br /> **5** = 未知|  
|**last_run_duration**|**int**|上次執行步驟的持續期間 (hhmmss)。|  
|**last_run_retries**|**int**|上次執行步驟時的命令重試次數。|  
|**last_run_date**|**int**|上次開始執行步驟的日期。|  
|**last_run_time**|**int**|上次開始執行步驟的時間。|  
|**proxy_id**|**int**|作業步驟的 Proxy。|  
  
## <a name="remarks"></a>備註  
 **sp_help_jobstep**處於**msdb**資料庫。  
  
## <a name="permissions"></a>Permissions  
 依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。 其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 如需這些角色權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。  
  
 成員**SQLAgentUserRole**只能檢視他們擁有之作業的作業步驟。  
  
## <a name="examples"></a>範例  
  
### <a name="a-return-information-for-all-steps-in-a-specific-job"></a>A. 傳回特定作業中所有步驟的資訊  
 下列範例會傳回名稱為 `Weekly Sales Data Backup` 之作業的所有作業步驟。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-information-about-a-specific-job-step"></a>B. 傳回特定作業步驟的資訊  
 下列範例會傳回名稱為 `Weekly Sales Data Backup` 之作業的第一個作業步驟的資訊。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
