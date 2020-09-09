---
description: sysmail_delete_principalprofile_sp (Transact-SQL)
title: sysmail_delete_principalprofile_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_principalprofile_sp_TSQL
- sysmail_delete_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_principalprofile_sp
ms.assetid: 8fc14700-e17a-4073-9a96-7fc23e775c69
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e5cfe34ff4bebc2e21517e6515b5ea2ebee3a37f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538468"
---
# <a name="sysmail_delete_principalprofile_sp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  移除資料庫使用者或使用公用或私人 Database Mail 設定檔之角色的權限。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>引數  
`[ @principal_id = ] principal_id` 這是要刪除之關聯的 **msdb** 資料庫中，資料庫使用者或角色的識別碼。 *principal_id* 是 **int**，預設值是 Null。 若要將公用設定檔設為私用設定檔，請提供主體識別碼 **0** 或主體名稱 **' public '**。 必須指定 *principal_id* 或 *principal_name* 。  
  
`[ @principal_name = ] 'principal_name'` 這是要刪除之關聯的 **msdb** 資料庫中，資料庫使用者或角色的名稱。 *principal_name* 是 **sysname**，預設值是 Null。 若要將公用設定檔設為私用設定檔，請提供主體識別碼 **0** 或主體名稱 **' public '**。 必須指定 *principal_id* 或 *principal_name* 。  
  
`[ @profile_id = ] profile_id` 這是要刪除之關聯的設定檔識別碼。 *profile_id* 是 **int**，預設值是 Null。 必須指定 *profile_id* 或 *profile_name* 。  
  
`[ @profile_name = ] 'profile_name'` 這是要刪除之關聯的設定檔名稱。 *profile_name* 是 **sysname**，預設值是 Null。 必須指定 *profile_id* 或 *profile_name* 。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 若要將公用設定檔設為私人設定檔，請為主體名稱提供 **' public '** ，或為主體識別碼提供 **0** 。  
  
 當移除使用者預設私人設定檔的權限，或移除預設公用設定檔的權限時，請特別小心。 如果沒有可用的預設設定檔， **sp_send_dbmail** 要求設定檔名稱做為引數。 因此，移除預設設定檔可能會導致 **sp_send_dbmail** 的呼叫失敗。 如需詳細資訊，請參閱 [sp_send_dbmail &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)。  
  
 預存程式 **sysmail_delete_principalprofile_sp** 位於 **msdb** 資料庫中，而且是由 **dbo** 架構所擁有。 如果目前的資料庫不是 **msdb**，就必須以三部分名稱執行程式。  
  
## <a name="permissions"></a>權限  
 此程式的執行許可權預設為 **系統管理員（sysadmin** ）固定伺服器角色的成員。  
  
## <a name="examples"></a>範例  
 下列範例示範如何刪除設定檔**AdventureWorks 系統管理員**與**msdb**資料庫中的登入 **>applicationuser**之間的關聯。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail 設定物件](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [&#40;Transact-sql&#41;的 Database Mail 預存程式 ](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
