---
title: sp_post_msx_operation （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_post_msx_operation
- sp_post_msx_operation_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_post_msx_operation
ms.assetid: 085deef8-2709-4da9-bb97-9ab32effdacf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d27a763efe79c9ab7f4809416b7bbc57f08e4044
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720258"
---
# <a name="sp_post_msx_operation-transact-sql"></a>sp_post_msx_operation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  將作業（資料列）插入目標伺服器的**sysdownloadlist**系統資料表中，以供下載和執行。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_post_msx_operation  
     [ @operation = ] 'operation'  
     [ , [ @object_type = ] 'object' ]   
     { , [ @job_id = ] job_id }   
     [ , [ @specific_target_server = ] 'target_server' ]   
     [ , [ @value = ] value ]  
     [ , [ @schedule_uid = ] schedule_uid ]  
```  
  
## <a name="arguments"></a>引數  
`[ @operation = ] 'operation'`已張貼作業的作業類型。 *operation*是**Varchar （64）**，沒有預設值。 有效的作業取決於*object_type*。  
  
|物件類型|作業|  
|-----------------|---------------|  
|**任務**|Insert<br /><br /> UPDATE<br /><br /> 刪除<br /><br /> START<br /><br /> STOP|  
|**伺服器**|RE-ENLIST<br /><br /> DEFECT<br /><br /> SYNC-TIME<br /><br /> SET-POLL|  
|**任務**|Insert<br /><br /> UPDATE<br /><br /> 刪除|  
  
`[ @object_type = ] 'object'`要為其張貼作業的物件類型。 有效的類型為 [**作業**]、[**伺服器**] 和 [**排程**]。 *物件*是**Varchar （64）**，預設值是**JOB**。  
  
`[ @job_id = ] job_id`作業套用的作業識別碼。 *job_id*是**uniqueidentifier**，沒有預設值。 **0x00**表示所有作業。 如果*物件*為**SERVER**，則不需要*job_id*。  
  
`[ @specific_target_server = ] 'target_server'`套用指定作業的目標伺服器名稱。 如果指定了*job_id* ，但未指定*target_server* ，則會針對作業的所有作業伺服器來張貼操作。 *target_server*是**Nvarchar （30）**，預設值是 Null。  
  
`[ @value = ] value`輪詢間隔（以秒為單位）。 *value* 是 **int**，預設值是 NULL。 只有在作業**設定**為 *[輪詢] 時，* 才指定此參數。  
  
`[ @schedule_uid = ] schedule_uid`作業所套用之排程的唯一識別碼。 *schedule_uid*是**uniqueidentifier**，沒有預設值。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 **sp_post_msx_operation**必須從**msdb**資料庫中執行。  
  
 **sp_post_msx_operation**一律可以安全地呼叫，因為它會先判斷目前的伺服器是否為多伺服器 Microsoft SQL Server 代理程式，如果是，*物件*是否為多伺服器作業。  
  
 在張貼作業之後，它會出現在**sysdownloadlist**資料表中。 建立和公佈作業之後，也必須通知目標伺服器 (TSX) 後續的作業變更。 這也可以利用下載清單加以完成。  
  
 我們強烈建議您利用 SQL Server Management Studio 來管理下載清單。 如需詳細資訊，請參閱[View Or Modify job](../../ssms/agent/view-or-modify-jobs.md)。  
  
## <a name="permissions"></a>權限  
 若要執行這個預存程式，使用者必須被授與**系統管理員（sysadmin** ）固定伺服器角色。  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_jobserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_delete_targetserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_resync_targetserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)   
 [sp_start_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_stop_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [sp_update_operator &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
