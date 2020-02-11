---
title: sp_help_maintenance_plan （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_maintenance_plan_TSQL
- sp_help_maintenance_plan
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_maintenance_plan
ms.assetid: e972a510-960e-41d6-93c5-c71cd581a585
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42a98fe7af16c4e8aab22d6ace02f359dfe02c54
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096198"
---
# <a name="sp_help_maintenance_plan-transact-sql"></a>sp_help_maintenance_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回指定維護計畫的相關資訊。 如果未指定計畫，這個預存程序會傳回所有維護計畫的相關資訊。  
  
> **注意：** 這個預存程式會與資料庫維護計畫搭配使用。 這項功能已被不使用這個預存程序的維護計畫所取代。 請使用這個程序來維護由舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級之安裝的資料庫維護計畫。  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_maintenance_plan [ [ @plan_id = ] 'plan_id' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @plan_id = ] 'plan\_id'`指定維護計畫的計畫識別碼。 *plan_id*是**UNIQUEIDENTIFIER**。 預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 None  
  
## <a name="result-sets"></a>結果集  
 如果指定了*plan_id* ， **sp_help_maintenance_plan**會傳回三個數據表：方案、資料庫和作業。  
  
### <a name="plan-table"></a>計畫資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|維護計畫識別碼。|  
|**plan_name**|**sysname**|維護計畫名稱。|  
|**date_created**|**datetime**|維護計畫的建立日期。|  
|**主人**|**sysname**|維護計畫的擁有者。|  
|**max_history_rows**|**int**|用來將維護計畫的記錄記載到系統資料表中，所配置的最大資料列數。|  
|**remote_history_server**|**int**|可以寫入記錄報表之遠端伺服器的名稱。|  
|**max_remote_history_rows**|**int**|在遠端伺服器系統資料表中，可寫入記錄報表的資料列最大配置列數。|  
|**user_defined_1**|**int**|預設值是 NULL。|  
|**user_defined_2**|**Nvarchar （100）**|預設值是 NULL。|  
|**user_defined_3**|**datetime**|預設值是 NULL。|  
|**user_defined_4**|**uniqueidentifier**|預設值是 NULL。|  
  
### <a name="database-table"></a>資料庫資料表  
  
|資料行名稱|描述|  
|-----------------|-----------------|  
|**database_name**|維護計畫所有相關資料庫的名稱。 *database_name*是**sysname**。|  
  
### <a name="job-table"></a>作業資料表  
  
|資料行名稱|描述|  
|-----------------|-----------------|  
|**job_id**|與維護計畫相關聯之所有作業的識別碼。 *job_id*是**uniqueidentifier**。|  
  
## <a name="remarks"></a>備註  
 **sp_help_maintenance_plan**是在**msdb**資料庫中。  
  
## <a name="permissions"></a>權限  
 只有**系統管理員（sysadmin** ）固定伺服器角色的成員，才能夠執行**sp_help_maintenance_plan**。  
  
## <a name="examples"></a>範例  
 這個範例說明 FAD6F2AB-3571-11D3-9D4A-00C04FB925FC 維護計畫的相關資訊。  
  
```  
EXECUTE   sp_help_maintenance_plan   
   N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC';  
```  
  
## <a name="see-also"></a>另請參閱  
 [維護計畫](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [資料庫維護計畫預存程式 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
