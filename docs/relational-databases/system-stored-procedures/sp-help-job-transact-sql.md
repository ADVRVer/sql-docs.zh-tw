---
title: sp_help_job (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_job_TSQL
- sp_help_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_job
ms.assetid: 8a8b6104-e0e4-4d07-a2c3-f4243ee0d6fa
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f60875014b4fe03833947bfed87ab42a23c79e32
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262981"
---
# <a name="sphelpjob-transact-sql"></a>sp_help_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 用來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的自動化活動之作業的相關資訊。  
  
 
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_job { [ @job_id = ] job_id  
[ @job_name = ] 'job_name' }   
     [ , [ @job_aspect = ] 'job_aspect' ]   
     [ , [ @job_type = ] 'job_type' ]   
     [ , [ @owner_login_name = ] 'login_name' ]   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @enabled = ] enabled ]   
     [ , [ @execution_status = ] status ]   
     [ , [ @date_comparator = ] 'date_comparison' ]   
     [ , [ @date_created = ] date_created ]   
     [ , [ @date_last_modified = ] date_modified ]   
     [ , [ @description = ] 'description_pattern' ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@job_id =**] *job_id*  
 作業識別碼。 *job_id*是**uniqueidentifier**，預設值是 NULL。  
  
 [ **@job_name =**] **'***job_name***'**  
 作業的名稱。 *job_name*是**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  若要檢視特定工作，可能是*job_id*或*job_name*必須指定。  省略兩者*job_id*和*job_name*傳回所有工作的相關資訊。
  
 [ **@job_aspect =**] **'***job_aspect***'**  
 要顯示的作業屬性。 *job_aspect*是**varchar(9)**，預設值是 NULL，而且可以是下列值之一。  
  
|Value|Description|  
|-----------|-----------------|  
|**ALL**|作業各方面的資訊|  
|**JOB**|作業資訊|  
|**排程**|排程資訊|  
|**STEPS**|作業步驟資訊|  
|**目標**|目標資訊|  
  
 [ **@job_type =**] **'***job_type***'**  
 這是要併入報表中的作業類型。 *job_type*是**varchar(12)**，預設值是 NULL。 *job_type*可以**本機**或**MULTI-SERVER**。  
  
 [ **@owner_login_name =**] **'***login_name***'**  
 作業擁有者的登入名稱。 *login_name*是**sysname**，預設值是 NULL。  
  
 [ **@subsystem =**] **'***subsystem***'**  
 子系統的名稱。 *子系統*是**nvarchar （40)**，預設值是 NULL。  
  
 [ **@category_name =**] **'***category***'**  
 類別目錄的名稱。 *類別*是**sysname**，預設值是 NULL。  
  
 [  **@enabled =**]*啟用*  
 這是一個數字，指出所顯示的資訊是關於已啟用或停用之作業。 *啟用*是**tinyint**，預設值是 NULL。 **1**表示已啟用的工作和**0**表示已停用的作業。  
  
 [  **@execution_status =**]*狀態*  
 作業的執行狀態。 *狀態*是**int**，預設值是 NULL，而且可以是下列值之一。  
  
|Value|描述|  
|-----------|-----------------|  
|**0**|只傳回未閒置或暫停的作業。|  
|**1**|執行中。|  
|**2**|正在等候執行緒。|  
|**3**|在重試之間。|  
|**4**|閒置。|  
|**5**|已暫停。|  
|**7**|正在執行完成動作。|  
  
 [ **@date_comparator =**] **'***date_comparison***'**  
 要在比較中使用的比較運算子*date_created*和*date_modified*。 *date_comparison*是**char （1)**，它可以 = \<，或 >。  
  
 [ **@date_created =**] *date_created*  
 作業的建立日期。 *date_created*是**datetime**，預設值是 NULL。  
  
 [ **@date_last_modified =**] *date_modified*  
 上次修改作業的日期。 *date_modified*是**datetime**，預設值是 NULL。  
  
 [ **@description =**] **'***description_pattern***'**  
 這是作業的描述。 *description_pattern*是**nvarchar （512)**，預設值是 NULL。 *description_pattern*可以包含 SQL Server 用於萬用字元模式比對。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 如果未不指定任何引數， **sp_help_job**傳回下列結果集。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|作業的唯一識別碼。|  
|**originating_server**|**nvarchar(30)**|作業的來源伺服器名稱。|  
|**name**|**sysname**|作業名稱。|  
|**enabled**|**tinyint**|指出是否啟用作業，以便執行。|  
|**描述**|**nvarchar(512)**|作業的描述。|  
|**start_step_id**|**int**|應該作為執行起點的作業步驟識別碼。|  
|**category**|**sysname**|作業類別目錄。|  
|**擁有者**|**sysname**|作業擁有者。|  
|**notify_level_eventlog**|**int**|**位元遮罩**指出在哪些情況之下通知事件應該在 Microsoft Windows 應用程式記錄檔記錄。 它可以是下列值之一：<br /><br /> **0** = 永不<br /><br /> **1** = 當作業成功時<br /><br /> **2** = 當作業失敗<br /><br /> **3** = 每當作業完成 （不論作業結果）|  
|**notify_level_email**|**int**|**位元遮罩**指出在哪些情況之下的通知電子郵件應該傳送作業完成時。 可能的值為一樣**notify_level_eventlog**。|  
|**notify_level_netsend**|**int**|**位元遮罩**指出在哪些情況之下網路訊息應該傳送作業完成時。 可能的值為一樣**notify_level_eventlog**。|  
|**notify_level_page**|**int**|**位元遮罩**指出在哪些情況之下一個頁面應該在作業完成時。 可能的值為一樣**notify_level_eventlog**。|  
|**notify_email_operator**|**sysname**|要通知的操作員電子郵件名稱。|  
|**notify_netsend_operator**|**sysname**|傳送網路訊息時所用的電腦或使用者名稱。|  
|**notify_page_operator**|**sysname**|傳送呼叫時所用的電腦或使用者名稱。|  
|**delete_level**|**int**|**位元遮罩**指出在哪些情況之下，應該刪除作業在作業完成時。 可能的值為一樣**notify_level_eventlog**。|  
|**date_created**|**datetime**|作業的建立日期。|  
|**date_modified**|**datetime**|上次修改作業的日期。|  
|**version_number**|**int**|作業的版本 (每次修改作業時，都會自動更新)。|  
|**last_run_date**|**int**|上次開始執行作業的日期。|  
|**last_run_time**|**int**|上次開始執行作業的時間。|  
|**last_run_outcome**|**int**|上次執行作業的輸出：<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **3** = 取消<br /><br /> **5** = 未知|  
|**next_run_date**|**int**|排程下一次執行作業的日期。|  
|**next_run_time**|**int**|排程下一次執行作業的時間。|  
|**next_run_schedule_id**|**int**|下次執行的排程識別碼。|  
|**current_execution_status**|**int**|目前的執行狀態。|  
|**current_execution_step**|**sysname**|作業中目前的執行步驟。|  
|**current_retry_attempt**|**int**|如果作業在執行中，且已重試這個步驟，這便是目前這次的重試。|  
|**has_step**|**int**|作業所擁有的作業步驟數目。|  
|**has_schedule**|**int**|作業所擁有的作業排程數目。|  
|**has_target**|**int**|作業所擁有的目標伺服器數目。|  
|**type**|**int**|作業類型。<br /><br /> 1 = 本機作業。<br /><br /> **2** = 多伺服器作業。<br /><br /> **0** = 作業已沒有目標伺服器。|  
  
 如果*job_id*或*job_name*指定，則**sp_help_job**傳回這些作業步驟、 工作排程和作業目標伺服器的其他結果集。  
  
 這是作業步驟的結果集。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|步驟的唯一 (針對這項作業) 識別碼。|  
|**step_name**|**sysname**|步驟的名稱。|  
|**subsystem**|**nvarchar(40)**|在其中執行步驟命令的子系統。|  
|**command**|**nvarchar(3200)**|要執行的命令。|  
|**flags**|**nvarchar(4000)**|**位元遮罩**來控制步驟行為的值。|  
|**cmdexec_success_code**|**int**|如**CmdExec**步驟中，這是成功命令的處理序結束碼。|  
|**on_success_action**|**nvarchar(4000)**|作業成功時要執行什麼動作。<br /><br /> **1** = 成功而結束。<br /><br /> **2** = 失敗而結束。<br /><br /> **3** = 移至下一個步驟。<br /><br /> **4** = 移至步驟。|  
|**on_success_step_id**|**int**|如果**on_success_action**是**4**，這表示要執行的下一個步驟。|  
|**on_fail_action**|**nvarchar(4000)**|步驟失敗時所採取的動作。 值為一樣**on_success_action**。|  
|**on_fail_step_id**|**int**|如果**on_fail_action**是**4**，這表示要執行的下一個步驟。|  
|**伺服器**|**sysname**|已保留。|  
|**database_name**|**sysname**|如果是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 步驟，這就是命令執行所在的資料庫。|  
|**database_user_name**|**sysname**|如果是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 步驟，這就是命令執行所在的資料庫使用者環境。|  
|**retry_attempts**|**int**|命令應該重試的最大次數 (如果沒有成功)，之後，便將步驟視為失敗。|  
|**retry_interval**|**int**|任何重試的間隔 (以分鐘為單位)。|  
|**os_run_priority**|**varchar(4000)**|已保留。|  
|**output_file_name**|**varchar(200)**|應該寫入命令輸出的檔案 ([!INCLUDE[tsql](../../includes/tsql-md.md)]和**CmdExec**只有步驟)。|  
|**last_run_outcome**|**int**|上次執行步驟的結果：<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **3** = 取消<br /><br /> **5** = 未知|  
|**last_run_duration**|**int**|步驟上次執行的持續時間 (以秒為單位)。|  
|**last_run_retries**|**int**|上次執行步驟時的命令重試次數。|  
|**last_run_date**|**int**|上次開始執行步驟的日期。|  
|**last_run_time**|**int**|上次開始執行步驟的時間。|  
|**proxy_id**|**int**|作業步驟的 Proxy。|  
  
 這是作業排程的結果集。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|排程的識別碼 (跨越所有作業而為唯一)。|  
|**schedule_name**|**sysname**|排程的名稱 (只對這項作業而為唯一)。|  
|**enabled**|**int**|排程是否為作用中 (**1**) 與否 (**0**)。|  
|**freq_type**|**int**|指出作業執行時間的值：<br /><br /> **1** = 一次<br /><br /> **4** = 每天<br /><br /> **8** = 每週<br /><br /> **16** = 每月<br /><br /> **32** = 每月，相對於**freq_interval**<br /><br /> **64** = 時執行**SQLServerAgent**服務啟動。|  
|**freq_interval**|**int**|執行作業的天數。 值取決於值**freq_type**。 如需詳細資訊，請參閱[sp_add_schedule &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_type**|**整數**|單位**freq_subday_interval**。 如需詳細資訊，請參閱[sp_add_schedule &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_interval**|**int**|數目**freq_subday_type**期間每次執行作業之間發生。 如需詳細資訊，請參閱[sp_add_schedule &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_relative_interval**|**int**|排程作業的次數**freq_interval**中每個月。 如需詳細資訊，請參閱[sp_add_schedule &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_recurrence_factor**|**int**|排程執行作業的間隔月數。|  
|**active_start_date**|**int**|開始執行作業的日期。|  
|**active_end_date**|**int**|停止執行作業的日期。|  
|**active_start_time**|**int**|在開始執行作業的時間**active_start_date。**|  
|**active_end_time**|**int**|在工作結束執行的時間**active_end_date**。|  
|**date_created**|**datetime**|排程的建立日期。|  
|**schedule_description**|**nvarchar(4000)**|排程的英文描述 (若要求的話)。|  
|**next_run_date**|**int**|排程下次執行作業的日期。|  
|**next_run_time**|**int**|排程下次執行作業的時間。|  
|**schedule_uid**|**uniqueidentifier**|排程的識別碼。|  
|**job_count**|**int**|傳回參考這份排程的作業數。|  
  
 這是作業目標伺服器的結果集。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|目標伺服器識別碼。|  
|**server_name**|**nvarchar(30)**|目標伺服器的電腦名稱。|  
|**enlist_date**|**datetime**|將目標伺服器編列到主要伺服器的日期。|  
|**last_poll_date**|**datetime**|目標伺服器前次輪詢主要伺服器的日期。|  
|**last_run_date**|**int**|在這部目標伺服器中上次開始執行作業的日期。|  
|**last_run_time**|**int**|在這部目標伺服器中上次開始執行作業的時間。|  
|**last_run_duration**|**int**|前次在這部目標伺服器執行作業的持續時間。|  
|**last_run_outcome**|**tinyint**|前次在這部伺服器執行作業的結果：<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **3** = 取消<br /><br /> **5** = 未知|  
|**last_outcome_message**|**nvarchar(1024)**|前次在這部目標伺服器執行作業的結果訊息。|  
  
## <a name="permissions"></a>Permissions  
 依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。 其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 如需這些角色權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)。  
  
 成員**SQLAgentUserRole**只能檢視他們所擁有的作業。 成員**sysadmin**， **SQLAgentReaderRole**，和**SQLAgentOperatorRole**可以檢視所有本機作業和多伺服器作業。  
  
## <a name="examples"></a>範例  
  
### <a name="a-list-information-for-all-jobs"></a>A. 列出所有作業的資訊  
 下列範例會執行不含參數的 `sp_help_job` 程序，來傳回 `msdb` 資料庫中目前所定義的所有作業。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-matching-a-specific-criteria"></a>B. 列出符合特定準則之作業的資訊  
 下列範例會列出啟用且執行作業的 `françoisa` 所擁有的多伺服器作業的作業資訊。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job   
   @job_type = N'MULTI-SERVER',  
   @owner_login_name = N'françoisa',  
   @enabled = 1,  
   @execution_status = 1 ;  
GO  
```  
  
### <a name="c-listing-all-aspects-of-information-for-a-job"></a>C. 列出作業各方面的資訊  
 下列範例會列出 `NightlyBackups` 作業各方面的資訊。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job  
    @job_name = N'NightlyBackups',  
    @job_aspect = N'ALL' ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_update_job &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
