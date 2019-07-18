---
title: sp_delete_schedule (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_schedule
- sp_delete_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_schedule
ms.assetid: 18b2c985-47b8-49c8-82d1-8a4af3d7d33a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7a2a4e8a7cf58f8c4519d15ae46e2b278fcd1383
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008954"
---
# <a name="spdeleteschedule-transact-sql"></a>sp_delete_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  刪除排程。  
 
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_delete_schedule { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @force_delete = ] force_delete  
```  
  
## <a name="arguments"></a>引數  
`[ @schedule_id = ] schedule_id` 要刪除之排程的排程識別碼。 *schedule_id*已**int**，預設值是 NULL。  
  
> **注意：** 任一*schedule_id*或是*schedule_name&lt*必須指定，但不可同時指定兩者。  
  
`[ @schedule_name = ] 'schedule_name'` 要刪除的排程名稱。 *schedule_name&lt*已**sysname**，預設值是 NULL。  
  
> **注意：** 任一*schedule_id*或是*schedule_name&lt*必須指定，但不可同時指定兩者。  
  
`[ @force_delete = ] force_delete` 指定是否排程附加至作業，此程序是否應該失敗。 *Force_delete* bit，預設值是**0**。 當*force_delete*是**0**，如果排程附加至作業，預存程序就會失敗。 當*force_delete*是**1**，不論排程是否附加至作業，都會刪除排程。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 依預設，如果排程附加至作業中，並無法刪除排程。 若要刪除附加至作業的排程，指定其值為**1** for *force_delete*。 刪除排程，並不會停止目前在執行中的作業。  
  
## <a name="permissions"></a>Permissions  
 依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。 其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 請注意，作業擁有者不需要也是排程擁有者，就可以將作業附加到排程，也可以從排程卸離作業。 不過，如果卸離之後不會在排程中留下任何作業，除非呼叫端是排程擁有者，否則無法刪除該排程。  
  
 如需這些角色權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。  
  
 只有成員**sysadmin**角色可以刪除作業排程是由另一位使用者所擁有。  
  
## <a name="examples"></a>範例  
  
### <a name="a-deleting-a-schedule"></a>A. 刪除排程  
 下列範例會刪除 `NightlyJobs` 排程。 如果這份排程附加至任何作業中，這個範例便不會刪除這份排程。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
### <a name="b-deleting-a-schedule-attached-to-a-job"></a>B. 刪除附加至作業的排程  
 下列範例會刪除 `RunOnce` 排程，不論排程是否附加至作業中都是如此。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = 'RunOnce',  
    @force_delete = 1;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [實作作業](../../ssms/agent/implement-jobs.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)  
  
  
