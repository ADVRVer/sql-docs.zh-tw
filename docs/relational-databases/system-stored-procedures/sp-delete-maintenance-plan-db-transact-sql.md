---
description: sp_delete_maintenance_plan_db (Transact-SQL)
title: sp_delete_maintenance_plan_db (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan_db_TSQL
- sp_delete_maintenance_plan_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan_db
- maintenance plans [SQL Server], deleting
- removing maintenance plan
- disassociating maintenance plan
ms.assetid: d1e8afb5-12ee-492b-a770-ba708ed7c8a4
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b3e6f99c99dbe65206c450aeeb2e935a7a5f0d25
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541804"
---
# <a name="sp_delete_maintenance_plan_db-transact-sql"></a>sp_delete_maintenance_plan_db (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  從指定的資料庫解除指定維護計畫的關聯。  
  
> [!NOTE]  
>  這個預存程序需搭配資料庫維護計畫一起使用。 這項功能已被不使用這個預存程序的維護計畫所取代。 請使用這個程序來維護由舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級之安裝的資料庫維護計畫。  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_delete_maintenance_plan_db [ @plan_id = ] 'plan_id' ,   
     [ @db_name = ] 'database_name'   
```  
  
## <a name="arguments"></a>引數  
`[ @plan_id = ] 'plan\_id'` 指定維護計畫識別碼。 *plan_id* 為 **uniqueidentifier**。  
  
`[ @db_name = ] 'database\_name'` 指定要從維護計畫中刪除的資料庫名稱。 *database_name* 為 **sysname**。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_delete_maintenance_plan_db** 必須從 **msdb** 資料庫執行。  
  
 **Sp_delete_maintenance_plan_db**預存程式會移除維護計畫與指定資料庫之間的關聯;它不會捨棄或損毀資料庫。  
  
 當 **sp_delete_maintenance_plan_db** 從維護計畫中移除最後一個資料庫時，預存程式也會刪除維護計畫。  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色的成員，才可以執行 **sp_delete_maintenance_plan_db**。  
  
## <a name="examples"></a>範例  
 刪除 **AdventureWorks2012** 資料庫中的維護計畫，此計畫先前是使用 **sp_add_maintenance_plan_db**新增的。  
  
```  
EXECUTE   sp_delete_maintenance_plan_db N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>另請參閱  
 [維護計畫](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [&#40;Transact-sql&#41;的資料庫維護計畫預存程式 ](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
