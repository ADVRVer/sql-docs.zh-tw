---
title: sp_add_schedule (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_schedule_TSQL
- sp_add_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_schedule
ms.assetid: 9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6fc52fd7af36d2238c53d8cbd877b7a6d43cd1dd
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591482"
---
# <a name="spaddschedule-transact-sql"></a>sp_add_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  建立可供任意數量的作業使用的排程。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_add_schedule [ @schedule_name = ] 'schedule_name'   
    [ , [ @enabled = ] enabled ]  
    [ , [ @freq_type = ] freq_type ]  
    [ , [ @freq_interval = ] freq_interval ]   
    [ , [ @freq_subday_type = ] freq_subday_type ]   
    [ , [ @freq_subday_interval = ] freq_subday_interval ]   
    [ , [ @freq_relative_interval = ] freq_relative_interval ]   
    [ , [ @freq_recurrence_factor = ] freq_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time = ] active_start_time ]   
    [ , [ @active_end_time = ] active_end_time ]   
    [ , [ @owner_login_name = ] 'owner_login_name' ]  
    [ , [ @schedule_uid = ] schedule_uid OUTPUT ]  
    [ , [ @schedule_id = ] schedule_id OUTPUT ]  
    [ , [ @originating_server = ] server_name ] /* internal */  
```  
  
## <a name="arguments"></a>引數  
 [  **@schedule_name =** ] **'**_schedule_name&lt_**'**  
 排程的名稱。 *schedule_name&lt*已**sysname**，沒有預設值。  
  
 [  **@enabled =** ]*啟用*  
 指出排程的目前狀態。 *已啟用*已**tinyint**，預設值是**1** （啟用）。 如果**0**，未啟用排程。 當未啟用排程時，不會依據這份排程來執行任何作業。  
  
 [ **@freq_type =** ] *freq_type*  
 指出將執行作業之時間的值。 *freq_type*已**int**，預設值是**0**，而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|一次|  
|**4**|每日|  
|**8**|每週|  
|**16**|每月|  
|**32**|每月，相對於*freq_interval*|  
|**64**|在 SQLServerAgent 服務啟動之時執行|  
|**128**|在電腦閒置之時執行|  
  
 [ **@freq_interval =** ] *freq_interval*  
 執行作業的天數。 *freq_interval*已**int**，預設值是**1**，而定的值*freq_type*。  
  
|值*freq_type*|在影響*freq_interval*|  
|---------------------------|--------------------------------|  
|**1** （一次）|*freq_interval*未使用。|  
|**4** （每天）|每隔*freq_interval*天。|  
|**8** （每週）|*freq_interval*是一或多個項目 （以 OR 邏輯運算子結合）：<br /><br /> **1** = 星期日<br /><br /> **2** = 星期一<br /><br /> **4** = 星期二<br /><br /> **8** = 星期三<br /><br /> **16** = 星期四<br /><br /> **32** = 星期五<br /><br /> **64** = 星期六|  
|**16** （每月）|在  *freq_interval*天的月份。|  
|**32** （每月相對）|*freq_interval*是下列其中之一：<br /><br /> **1** = 星期日<br /><br /> **2** = 星期一<br /><br /> **3** = 星期二<br /><br /> **4** = 星期三<br /><br /> **5** = 星期四<br /><br /> **6** = 星期五<br /><br /> **7** = 星期六<br /><br /> **8** = 日<br /><br /> **9** = 工作日<br /><br /> **10** = 週末|  
|**64** （當 SQLServerAgent 服務啟動時）|*freq_interval*未使用。|  
|**128**|*freq_interval*未使用。|  
  
 [ **@freq_subday_type =** ] *freq_subday_type*  
 指定的單位*freq_subday_interval*。 *freq_subday_type*已**int**，預設值是**0**，而且可以是下列值之一。  
  
|值|描述 (單位)|  
|-----------|--------------------------|  
|**0x1**|在指定的時間|  
|**0x2**|秒|  
|**0x4**|Minutes|  
|**0x8**|小時|  
  
 [ **@freq_subday_interval =** ] *freq_subday_interval*  
 數目*freq_subday_type*期間每次執行作業之間發生。 *freq_subday_interval*已**int**，預設值是**0**。 注意：間隔應超過 10 秒。 *freq_subday_interval*在這些情況下會忽略其中*freq_subday_type*等於**1**。  
  
 [ **@freq_relative_interval =** ] *freq_relative_interval*  
 作業的次數*freq_interval*每個月中，如果*freq_interval*是 32 （每月相對）。 *freq_relative_interval*已**int**，預設值是**0**，而且可以是下列值之一。 *freq_relative_interval*在這些情況下會忽略其中*freq_type*不等於 32。  
  
|值|描述 (單位)|  
|-----------|--------------------------|  
|**1**|第一個|  
|**2**|第二個|  
|**4**|第三個|  
|**8**|第四個|  
|**16**|最後一個|  
  
 [ **@freq_recurrence_factor =** ] *freq_recurrence_factor*  
 作業的各排程執行之間的週數或月數。 *freq_type*才會使用*freq_type*是**8**， **16**，或**32**。 *freq_type*已**int**，預設值是**0**。  
  
 [ **@active_start_date =** ] *active_start_date*  
 可以開始執行作業的日期。 *active_start_date*已**int**，預設值是 NULL，表示今天的日期。 日期格式為 YYYYMMDD。 如果*active_start_date*不是 NULL，日期必須大於或等於 19900101。  
  
 建立排程之後，檢閱開始日期，並確認該日期正確。 如需詳細資訊，請參閱 「 排程開始日期 」 一節中[建立及附加排程至作業](../../ssms/agent/create-and-attach-schedules-to-jobs.md)。  
  
 若為每週或每月排程，代理程式會對 active_start_date 已是過去日期予以忽略，而將改為使用目前的日期。 使用 sp_add_schedule 建立 SQL 代理程式排程時，有一個選項可指定 active_start_date 參數，表示將要開始執行作業的日期。 如果排程類型是每週或每月，而且 active_start_date 參數設定為過去的日期，便會忽略 active_start_date 參數，並使用目前的日期做為 active_start_date。  
  
 [ **@active_end_date =** ] *active_end_date*  
 可以停止執行作業的日期。 *active_end_date*已**int**，預設值是**99991231**，這表示年 12 月 31 日至 9999。 格式為 YYYYMMDD。  
  
 [ **@active_start_time =** ] *active_start_time*  
 之間任何一天的時間*active_start_date*並*active_end_date*開始執行作業。 *active_start_time*已**int**，預設值是**000000**，這表示上午 12:00:00 必須用 HHMMSS 格式來輸入。  
  
 [ **@active_end_time =** ] *active_end_time*  
 之間任何一天的時間*active_start_date*並*active_end_date*結束執行作業。 *active_end_time*已**int**，預設值是**235959**，這表示下午 11:59:59 必須用 HHMMSS 格式來輸入。  
  
 [ **@owner_login_name**=] **'**_owner_login_name_**'**  
 擁有排程之伺服器主體的名稱。 *owner_login_name*已**sysname**，預設值是 NULL，表示排程建立者所擁有。  
  
 [ **@schedule_uid**=] _schedule_uid_**輸出**  
 排程的唯一識別碼。 *schedule_uid*類型的變數**uniqueidentifier**。  
  
 [ **@schedule_id**=] _schedule_id_**輸出**  
 排程的識別碼。 *schedule_id*類型的變數**int**。  
  
 [ **@originating_server**= ] *server_name*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供了一種簡單的圖形方式供您管理各項作業，建議您利用這個方式來建立和管理作業基礎結構。  
  
## <a name="permissions"></a>Permissions  
 依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。 其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 如需這些角色權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。  
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-schedule"></a>A. 建立排程  
 下列範例會建立一份名稱為 `RunOnce` 的排程。 這份排程會在建立排程當日的 `23:30` 執行一次。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_schedule  
    @schedule_name = N'RunOnce',  
    @freq_type = 1,  
    @active_start_time = 233000 ;  
  
GO  
```  
  
### <a name="b-creating-a-schedule-attaching-the-schedule-to-multiple-jobs"></a>B. 建立一份排程，將排程附加至多項作業  
 下列範例會建立一份名稱為 `NightlyJobs` 的排程。 每天伺服器時間到了 `01:00` 時，就會開始執行使用這份排程的作業。 這個範例會將排程附加至 `BackupDatabase` 作業和 `RunReports` 作業上。  
  
> [!NOTE]  
>  這個範例假設 `BackupDatabase` 作業和 `RunReports` 作業都已經存在。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_add_schedule  
    @schedule_name = N'NightlyJobs' ,  
    @freq_type = 4,  
    @freq_interval = 1,  
    @active_start_time = 010000 ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'BackupDatabase',  
   @schedule_name = N'NightlyJobs' ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'RunReports',  
   @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立及附加排程至作業](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [排程的作業](../../ssms/agent/schedule-a-job.md)   
 [建立排程](../../ssms/agent/create-a-schedule.md)   
 [SQL Server Agent 預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_jobschedule &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_update_schedule &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
