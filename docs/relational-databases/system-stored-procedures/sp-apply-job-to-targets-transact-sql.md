---
title: sp_apply_job_to_targets (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_apply_job_to_targets
- sp_apply_job_to_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_apply_job_to_targets
ms.assetid: 4a3e9173-7e3c-4100-a9ac-2f5d2c60a8b0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 192747d920f92681617d0dc19cc562e52e9c310e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47641710"
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
 [ **@job_id =**] *job_id*  
 要套用至指定目標伺服器或目標伺服器群組之作業的作業識別碼。 *job_id*已**uniqueidentifier**，預設值是 NULL。  
  
 [ **@job_name =**] **'***job_name***'**  
 要套用至指定的相關目標伺服器或目標伺服器群組的作業名稱。 *job_name*已**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  任一*job_id*或是*job_name*必須指定，但不可同時指定兩者。  
  
 [ **@target_server_groups =**]  **'***target_server_groups***'**  
 要套用指定作業的目標伺服器群組清單 (以逗號分隔)。 *target_server_groups*已 **& lt;languagekeyword>nvarchar(2048)</languagekeyword&gt**，預設值是 NULL。  
  
 [ **@target_servers=** ] **'***target_servers***'**  
 要套用指定作業的目標伺服器清單 (以逗號分隔)。 *target_servers*已 **& lt;languagekeyword>nvarchar(2048)</languagekeyword&gt**，預設值是 NULL。  
  
 [  **@operation=** ] **'***作業***'**  
 這是指應該將指定的作業套用在指定的目標伺服器或目標伺服器群組上，還是應該從其中移除指定的作業。 *作業*已**varchar(7)**，預設值是 APPLY。 有效的作業**套用**並**移除**。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_apply_job_to_targets**提供多部目標伺服器，輕鬆地套用 （或移除） 作業，並會於呼叫替代**sp_add_jobserver** (或**sp_delete_jobserver**)一次針對每部目標伺服器所需。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
