---
title: sp_purge_jobhistory (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_purge_jobhistory_TSQL
- sp_purge_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_purge_jobhistory
ms.assetid: 237f9bad-636d-4262-9bfb-66c034a43e88
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3ce9b0972bc95a927729f55e10e329cddb2993c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67896464"
---
# <a name="sppurgejobhistory-transact-sql"></a>sp_purge_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  移除作業的記錄。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_purge_jobhistory   
   {   [ @job_name = ] 'job_name' |   
     | [ @job_id = ] job_id }  
   [ , [ @oldest_date = ] oldest_date ]  
```  
  
## <a name="arguments"></a>引數  
`[ @job_name = ] 'job_name'` 若要刪除記錄之工作的名稱。 *job_name*已**sysname**，預設值是 NULL。 任一*job_id*或是*job_name*必須指定，但不可同時指定兩者。  
  
> [!NOTE]  
>  成員**sysadmin**固定伺服器角色或成員**SQLAgentOperatorRole**固定的資料庫角色可以執行**sp_purge_jobhistory**但未指定*job_name*或是*job_id*。 當**sysadmin**使用者未指定這些引數，指定時間內會刪除所有本機作業和多伺服器作業的作業記錄*oldest_date*。 當**SQLAgentOperatorRole**使用者未指定這些引數，指定時間內會刪除所有本機作業的作業記錄*oldest_date*。  
  
`[ @job_id = ] job_id` 作業識別碼是要刪除記錄的作業。 *job_id*已**uniqueidentifier**，預設值是 NULL。 任一*job_id*或是*job_name*必須指定，但不可同時指定兩者。 請參閱說明中的注意事項 **@job_name** 如需**sysadmin**或是**SQLAgentOperatorRole**使用者可以使用這個引數。  
  
`[ @oldest_date = ] oldest_date` 要保留在歷程記錄的最舊記錄。 *oldest_date*已**datetime**，預設值是 NULL。 當*oldest_date*指定，則**sp_purge_jobhistory**只會移除比指定的值還舊的記錄。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 當**sp_purge_jobhistory**已順利完成，將會傳回訊息。  
  
## <a name="permissions"></a>Permissions  
 根據預設，只有成員**sysadmin**固定的伺服器角色或**SQLAgentOperatorRole**固定的資料庫角色可以執行這個預存程序。 成員**sysadmin**可以清除所有本機作業和多伺服器作業的作業記錄。 成員**SQLAgentOperatorRole**可以清除只所有本機作業的作業記錄。  
  
 其他使用者，包括成員**SQLAgentUserRole**和成員**SQLAgentReaderRole**，必須明確被授與 EXECUTE 權限上**sp_purge_jobhistory**. 被授與此預存程序的 EXECUTE 權限之後，這些使用只能清除他們自己的作業記錄。  
  
 **SQLAgentUserRole**， **SQLAgentReaderRole**，並**SQLAgentOperatorRole**固定的資料庫角色都處於**msdb**資料庫。 如需有關其權限的詳細資訊，請參閱 < [SQL Server Agent 固定資料庫角色](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。  
  
## <a name="examples"></a>範例  
  
### <a name="a-remove-history-for-a-specific-job"></a>A. 移除特定作業的記錄  
 下列範例會移除名稱為 `NightlyBackups` 之作業的記錄。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-remove-history-for-all-jobs"></a>B. 移除所有作業的記錄  
  
> [!NOTE]  
>  只有成員**sysadmin**固定伺服器角色和成員**SQLAgentOperatorRole**可以移除所有作業記錄。 當**sysadmin**使用者執行這個預存程序，不含任何參數，會清除所有本機作業和多伺服器作業的作業記錄。 當**SQLAgentOperatorRole**使用者執行此預存程序，不含任何參數，會清除只所有本機作業的作業記錄。  
  
 下列範例會執行不含任何參數的程序來移除所有記錄。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [GRANT 物件權限 &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
  
