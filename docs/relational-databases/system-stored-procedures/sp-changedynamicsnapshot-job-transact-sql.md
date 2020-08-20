---
description: sp_changedynamicsnapshot_job (Transact-SQL)
title: sp_changedynamicsnapshot_job (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedynamicsnapshot_job
- sp_changedynamicsnapshot_job_TSQL
helpviewer_keywords:
- sp_changedynamicsnapshot_job
ms.assetid: ea0dacd2-a5fd-42f4-88dd-7d289b0ae017
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 73406c2860dbff4dfb5f6488a2195a9f00be4bc6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464445"
---
# <a name="sp_changedynamicsnapshot_job-transact-sql"></a>sp_changedynamicsnapshot_job (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  修改利用參數化資料列篩選器來產生發行集訂閱快照集的代理程式作業。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_changedynamicsnapshot_job [ @publication = ] 'publication'  
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]  
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]  
    [ , [ @frequency_type = ] frequency_type ]   
    [ , [ @frequency_interval = ] frequency_interval ]   
    [ , [ @frequency_subday = ] frequency_subday ]   
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]   
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]   
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]   
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'` 這是發行集的名稱。 *發行* 集是 **sysname**，沒有預設值。  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'` 這是要變更的快照集作業名稱。 *dynamic_snapshot_jobname*是 **sysname**，預設值是 N '% '。 如果指定 *dynamic_snapshot_jobid* ，您必須使用 *dynamic_snapshot_jobname*的預設值。  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'` 這是要變更的快照集作業識別碼。 *dynamic_snapshot_jobid* 是 **uniqueidentifier**，預設值是 Null。 如果指定 *dynamic_snapshot_jobname*，您必須使用 *dynamic_snapshot_jobid*的預設值。  
  
`[ @frequency_type = ] frequency_type` 這是代理程式的排程頻率。 *frequency_type* 是 **int**，而且可以是下列其中一個值。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|一次性|  
|**2**|隨選|  
|**4**|每日|  
|**8**|每週|  
|**16**|每月|  
|**32**|每月相對|  
|**64**|自動啟動|  
|**128**|重複執行|  
|NULL (預設值)||  
  
`[ @frequency_interval = ] frequency_interval` 代理程式執行的天數。 *frequency_interval* 是 **int**，而且可以是下列其中一個值。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|星期日|  
|**2**|星期一|  
|**3**|Tuesday|  
|**4**|星期三|  
|**5**|Thursday|  
|**6**|星期五|  
|**7**|星期六|  
|**8**|天|  
|**9**|工作日|  
|**10**|週末|  
|NULL (預設值)||  
  
`[ @frequency_subday = ] frequency_subday` 在定義的期間內，重新排程的頻率。 *frequency_subday* 是 **int**，而且可以是下列其中一個值。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|單次|  
|**2**|Second|  
|**4**|Minute|  
|**8**|小時|  
|NULL (預設值)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 這是 *frequency_subday*的間隔。 *frequency_subday_interval* 是 **int**，預設值是 Null。  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` 這是合併代理程式執行的日期。 當 *frequency_type* 設定為 **32** (每月相對) 時，就會使用這個參數。 *frequency_relative_interval* 是 **int**，而且可以是下列其中一個值。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|First|  
|**2**|Second|  
|**4**|Third|  
|**8**|第四個|  
|**16**|Last|  
|NULL (預設值)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 這是 *frequency_type*所用的迴圈因數。 *frequency_recurrence_factor* 是 **int**，預設值是 Null。  
  
`[ @active_start_date = ] active_start_date` 這是第一次排程合併代理程式的日期，格式為 YYYYMMDD。 *active_start_date* 是 **int**，預設值是 Null。  
  
`[ @active_end_date = ] active_end_date` 這是排程停止合併代理程式的日期，格式為 YYYYMMDD。 *active_end_date* 是 **int**，預設值是 Null。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` 這是第一次排程合併代理程式的當日時間，格式為 HHMMSS。 *active_start_time_of_day* 是 **int**，預設值是 Null。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` 這是排程合併代理程式停止的當日時間，格式為 HHMMSS。 *active_end_time_of_day* 是 **int**，預設值是 Null。  
  
`[ @job_login = ] 'job_login'` 這是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 使用參數化資料列篩選器來產生訂閱的快照集時，用來執行快照集代理程式的 Windows 帳戶。 *job_login* 是 **Nvarchar (257) **，預設值是 Null。  
  
`[ @job_password = ] 'job_password'` 這是使用參數化資料列篩選器來產生訂閱的快照集時，用來執行快照集代理程式之 Windows 帳戶的密碼。 *job_password* 是 **Nvarchar (257) **，預設值是 Null。  
  
> [!IMPORTANT]  
>  可能的話，會在執行階段提示使用者輸入安全性認證。 如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_changedynamicsnapshot_job** 用於具有參數化資料列篩選器的發行集之合併式複寫中。  
  
 變更代理程式的登入或密碼之後，您必須先停止並重新啟動代理程式，變更才會生效。  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色或 **db_owner** 固定資料庫角色的成員，才能夠執行 **sp_changedynamicsnapshot_job**。  
  
## <a name="see-also"></a>另請參閱  
 [檢視及修改複寫安全性設定](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
  
