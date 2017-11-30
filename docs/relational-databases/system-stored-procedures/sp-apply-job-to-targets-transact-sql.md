---
title: "sp_apply_job_to_targets (TRANSACT-SQL) |Microsoft 文件"
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
- sp_apply_job_to_targets
- sp_apply_job_to_targets_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_apply_job_to_targets
ms.assetid: 4a3e9173-7e3c-4100-a9ac-2f5d2c60a8b0
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f0b538c726a324709c35807c8e0f6bdc8bc3b607
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="spapplyjobtotargets-transact-sql"></a>sp_apply_job_to_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  將作業套用在一或多部目標伺服器上，或套用在屬於一或多個目標伺服器群組的目標伺服器上。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_apply_job_to_targets { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]   
     [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>引數  
 [  **@job_id =**] *job_id*  
 要套用至指定目標伺服器或目標伺服器群組之作業的作業識別碼。 *job_id*是**uniqueidentifier**，預設值是 NULL。  
  
 [  **@job_name =**] **'***job_name***'**  
 要套用至指定的相關目標伺服器或目標伺服器群組的作業名稱。 *job_name*是**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  任一*job_id*或*job_name*必須指定，但不可同時指定兩者。  
  
 [  **@target_server_groups =**] **'***target_server_groups***'**  
 要套用指定作業的目標伺服器群組清單 (以逗號分隔)。 *target_server_groups*是**nvarchar(2048)**，預設值是 NULL。  
  
 [  **@target_servers=** ] **'***target_servers***'**  
 要套用指定作業的目標伺服器清單 (以逗號分隔)。 *target_servers*是**nvarchar(2048)**，預設值是 NULL。  
  
 [  **@operation=** ] **'***作業***'**  
 這是指應該將指定的作業套用在指定的目標伺服器或目標伺服器群組上，還是應該從其中移除指定的作業。 *作業*是**varchar(7)**，預設值是 APPLY。 有效的作業為**套用**和**移除**。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_apply_job_to_targets**提供多部目標伺服器，輕鬆地套用 （或移除） 作業，並於呼叫替代**sp_add_jobserver** (或**sp_delete_jobserver**) 所需的每個目標伺服器可享有一次。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色可以執行此程序。  
  
## <a name="examples"></a>範例  
 下列範例會將先前建立的 `Backup Customer Information` 作業套用在 `Servers Maintaining Customer Information` 群組中的所有目標伺服器上。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_apply_job_to_targets  
    @job_name = N'Backup Customer Information',  
    @target_server_groups = N'Servers Maintaining Customer Information',   
    @operation = N'APPLY' ;  
GO  
```  
  
## <a name="see-also"></a>請參閱  
 [sp_add_jobserver &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
