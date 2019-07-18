---
title: sp_addpullsubscription_agent & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpullsubscription_agent
- sp_addpullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addpullsubscription_agent
ms.assetid: b9c2eaed-6d2d-4b78-ae9b-73633133180b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 220e21713935409d7d85ecd156524883dbbace08
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022460"
---
# <a name="spaddpullsubscriptionagent-transact-sql"></a>sp_addpullsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
 
  加入一項新排程的代理程式作業，以便用來同步處理提取訂閱與交易式發行集。 這個預存程序執行於訂閱資料庫的訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_addpullsubscription_agent [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]          , [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor = ] 'distributor' ]  
    [ , [ @distribution_db = ] 'distribution_db' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]  
    [ , [ @distributor_login = ] 'distributor_login' ]  
    [ , [ @distributor_password = ] 'distributor_password' ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @distribution_jobid = ] distribution_jobid OUTPUT ]  
    [ , [ @encrypted_distributor_password = ] encrypted_distributor_password ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @ftp_address = ] 'ftp_address' ]  
    [ , [ @ftp_port = ] ftp_port ]  
    [ , [ @ftp_login = ] 'ftp_login' ]  
    [ , [ @ftp_password = ] 'ftp_password' ]  
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]  
    [ , [ @working_directory = ] 'working_directory' ]  
    [ , [ @use_ftp = ] 'use_ftp' ]  
    [ , [ @publication_type = ] publication_type ]  
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @offloadagent = ] 'remote_agent_activation' ]  
    [ , [ @offloadserver = ] 'remote_agent_server_name']  
    [ , [ @job_name = ] 'job_name' ]  
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>引數  
`[ @publisher = ] 'publisher'` 是 「 發行者 」 的名稱。 *發行者*已**sysname**，沒有預設值。  
  
`[ @publisher_db = ] 'publisher_db'_` 是發行者資料庫的名稱。 *publisher_db*已**sysname**，預設值是 NULL。 *publisher_db* Oracle 發行者會忽略。  
  
`[ @publication = ] 'publication'` 是發行集名稱。 *發行集*已**sysname**，沒有預設值。  
  
`[ @subscriber = ] 'subscriber'` 是訂閱者的名稱。 *訂閱者*已**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  這個參數已被取代，維護它的目的，只是為了與舊版的指令碼相容。  
  
`[ @subscriber_db = ] 'subscriber_db'` 是訂閱資料庫的名稱。 *subscriber_db*已**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  這個參數已被取代，維護它的目的，只是為了與舊版的指令碼相容。  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` 是同步處理時，連接到訂閱者時要使用的安全性模式。 *subscriber_security_mode*已**int、** 預設值是 NULL。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證。 **1**指定 Windows 驗證。  
  
> [!NOTE]  
>  這個參數已被取代，維護它的目的，只是為了與舊版的指令碼相容。 散發代理程式一律是利用 Windows 驗證來連接到本機訂閱者。 如果 NULL 以外的值或**1**指定這個參數，會傳回一則警告訊息。  
  
`[ @subscriber_login = ] 'subscriber_login'` 這是訂閱者登入同步處理時，連接到訂閱者時使用。*subscriber_login*是**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  這個參數已被取代，維護它的目的，只是為了與舊版的指令碼相容。 如果指定了這個參數值，便會傳回警告訊息，但會忽略這個值。  
  
`[ @subscriber_password = ] 'subscriber_password'` 這是訂閱者密碼。 *subscriber_password* ，便須*subscriber_security_mode*設定為**0**。 *subscriber_password*已**sysname**，預設值是 NULL。 如果使用訂閱者密碼，它會自動加密。  
  
> [!NOTE]  
>  這個參數已被取代，維護它的目的，只是為了與舊版的指令碼相容。 如果指定了這個參數值，便會傳回警告訊息，但會忽略這個值。  
  
`[ @distributor = ] 'distributor'` 是散發者的名稱。 *散發者*已**sysname**，預設值是所指定的值*發行者*。  
  
`[ @distribution_db = ] 'distribution_db'` 是散發資料庫的名稱。 *distribution_db*已**sysname**，預設值是 NULL。  
  
`[ @distributor_security_mode = ] distributor_security_mode` 是，連接到散發者時同步處理時所要使用的安全性模式。 *distributor_security_mode*已**int**，預設值是**1**。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證。 **1**指定 Windows 驗證。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` 是，連接到散發者時同步處理時所要使用的散發者登入。 *distributor_login* ，便須*distributor_security_mode*設定為**0**。 *distributor_login*已**sysname**，預設值是 NULL。  
  
`[ @distributor_password = ] 'distributor_password'` 這是散發者密碼。 *distributor_password* ，便須*distributor_security_mode*設定為**0**。 *distributor_password*已**sysname**，預設值是 NULL。  
  
> [!IMPORTANT]  
>  請勿使用空白密碼。 請使用增強式密碼。 可能的話，會在執行階段提示使用者輸入安全性認證。 如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。  
  
`[ @optional_command_line = ] 'optional_command_line'` 是選擇性的命令提示字元，提供給 「 散發代理程式。 例如， **-DefinitionFile** C:\Distdef.txt 或 **-CommitBatchSize** 10。 *optional_command_line*已**nvarchar(4000)** ，預設值是空字串。  
  
`[ @frequency_type = ] frequency_type` 是用來排程散發代理程式的頻率。 *frequency_type*已**int**，而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|一次|  
|**2** (預設值)|視需要|  
|**4**|每日|  
|**8**|每週|  
|**16**|每月|  
|**32**|每月相對|  
|**64**|自動啟動|  
|**128**|重複執行|  
  
> [!NOTE]  
>  指定的值是**64**會導致散發代理程式以連續模式執行。 這對應於設定 **-連續**代理程式參數。 如需詳細資訊，請參閱 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)。  
  
`[ @frequency_interval = ] frequency_interval` 要套用至所設定之頻率的值*frequency_type*。 *frequency_interval*已**int**，預設值是 1。  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` 這是散發代理程式的日期。 使用這個參數時*frequency_type*設為**32** （每月相對）。 *frequency_relative_interval*已**int**，而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**1** (預設值)|第一個|  
|**2**|第二個|  
|**4**|第三個|  
|**8**|第四個|  
|**16**|最後一個|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 所使用的循環因數*frequency_type*。 *frequency_recurrence_factor*已**int**，預設值是**1**。  
  
`[ @frequency_subday = ] frequency_subday` 已定義的期間重新排程的頻率。 *frequency_subday*已**int**，而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**1** (預設值)|一次|  
|**2**|第二個|  
|**4**|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 間隔*frequency_subday*。 *frequency_subday_interval*已**int**，預設值是**1**。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` 散發代理程式時第一天的排程時間，格式為 HHMMSS。 *active_start_time_of_day*已**int**，預設值是**0**。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` 是 「 散發代理程式停止的當日時間排程，格式為 HHMMSS。 *active_end_time_of_day*已**int**，預設值是**0**。  
  
`[ @active_start_date = ] active_start_date` 是 「 散發代理程式時第一個排程的日期，格式為 YYYYMMDD。 *active_start_date*已**int**，預設值是**0**。  
  
`[ @active_end_date = ] active_end_date` 是 「 散發代理程式停止的日期排程，格式為 YYYYMMDD。 *active_end_date*已**int**，預設值是**0**。  
  
`[ @distribution_jobid = ] _distribution_jobidOUTPUT` 是此作業之散發代理程式的識別碼。 *distribution_jobid*已**二進位 （16)** ，預設值是 NULL，它是一個 OUTPUT 參數。  
  
`[ @encrypted_distributor_password = ] encrypted_distributor_password` 設定*encrypted_distributor_password*不受支援。 嘗試將這個**位元**參數來**1**會導致錯誤。  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` 為訂用帳戶是否可以透過同步[!INCLUDE[msCoName](../../includes/msconame-md.md)]Synchronization Manager。 *enabled_for_syncmgr*已**nvarchar(5)** ，預設值是 FALSE。 如果**false**，訂用帳戶未註冊使用 Synchronization Manager。 如果**真**，訂用帳戶使用 Synchronization Manager 註冊，並可以同步處理，而不啟動[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。  
  
`[ @ftp_address = ] 'ftp_address'` 基於回溯相容性。  
  
`[ @ftp_port = ] ftp_port` 基於回溯相容性。  
  
`[ @ftp_login = ] 'ftp_login'` 基於回溯相容性。  
  
`[ @ftp_password = ] 'ftp_password'` 基於回溯相容性。  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'_` 指定替代快照集資料夾的位置。 *alternate_snapshot_folder*已**nvarchar(255)** ，預設值是 NULL。  
  
`[ @working_directory = ] 'working_director'` 是用來儲存發行集的資料和結構描述檔案的工作目錄的名稱。 *working_directory*已**nvarchar(255)** ，預設值是 NULL。 這個名稱應該用 UNC 格式來指定。  
  
`[ @use_ftp = ] 'use_ftp'` 指定利用 FTP 而不是一般的通訊協定來擷取快照集。 *use_ftp*已**nvarchar(5)** ，預設值是 FALSE。  
  
`[ @publication_type = ] publication_type` 指定發行集的複寫類型。 *publication_type*已**tinyint**預設值是**0**。 如果**0**，發行集是交易類型。 如果**1**，發行集是快照集類型。 如果**2**，發行集是合併類型。  
  
`[ @dts_package_name = ] 'dts_package_name'` 指定 DTS 封裝的名稱。 *dts_package_name*已**sysname**預設值是 NULL。 例如，若要指定 `DTSPub_Package` 封裝，這個參數便是 `@dts_package_name = N'DTSPub_Package'`。  
  
`[ @dts_package_password = ] 'dts_package_password'` 如果有的話，請在封裝中，指定的密碼。 *dts_package_password*已**sysname**預設值是 NULL，這表示密碼不是封裝。  
  
> [!NOTE]  
>  您必須指定密碼，如果*dts_package_name*指定。  
  
`[ @dts_package_location = ] 'dts_package_location'` 指定封裝位置。 *dts_package_location*已**nvarchar(12)** ，預設值是**訂閱者**。 封裝位置可以是**散發者端**或是**訂閱者**。  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  遠端代理程式啟用已被取代，不再受到支援。 支援這個參數的目的，只是為了與舊版的指令碼相容。 設定*remote_agent_activation&lt*以外的值來**false**會產生錯誤。  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  遠端代理程式啟用已被取代，不再受到支援。 支援這個參數的目的，只是為了與舊版的指令碼相容。 設定*remote_agent_server_name*為任何非 NULL 值會產生錯誤。  
  
`[ @job_name = ] 'job_name'` 是現有的代理程式作業名稱。 *job_name*已**sysname**，預設值是 NULL。 只有在訂閱將利用現有的作業來同步處理，而不用新建立的作業 (預設值) 時，才指定這個參數。 如果您不屬於**sysadmin**固定伺服器角色，您必須指定*job_login*並*job_password*當您指定*job_name*.  
  
`[ @job_login = ] 'job_login'` 是執行代理程式的 Windows 帳戶的登入。 *job_login*已**nvarchar(257)** ，沒有預設值。 通往訂閱者的代理程式連接一律使用這個 Windows 帳戶。  
  
`[ @job_password = ] 'job_password'` 這是代理程式所執行的 Windows 帳戶的密碼。 *job_password*已**sysname**，沒有預設值。  
  
> [!IMPORTANT]  
>  可能的話，會在執行階段提示使用者輸入安全性認證。 如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **@ internet_login**用於快照式複寫和異動複寫。  
  
## <a name="example"></a>範例  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_addpullsubscription_agent**。  
  
## <a name="see-also"></a>另請參閱  
 [建立提取訂閱](../../relational-databases/replication/create-a-pull-subscription.md)   
 [訂閱發行集](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
