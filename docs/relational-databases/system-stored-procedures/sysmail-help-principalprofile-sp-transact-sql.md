---
description: sysmail_help_principalprofile_sp (Transact-SQL)
title: sysmail_help_principalprofile_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_principalprofile_sp_TSQL
- sysmail_help_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_principalprofile_sp
ms.assetid: 0cfd6464-09c7-4f03-9d25-58001c096a9e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8325480c2869f9b3e35caab51935eba36d888afb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488954"
---
# <a name="sysmail_help_principalprofile_sp-transact-sql"></a>sysmail_help_principalprofile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  列出 Database Mail 設定檔和資料庫主體間之關聯的相關資訊。  
  
 
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sysmail_help_principalprofile_sp [ {   [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ]  
    [ [ , ] {   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ]  
```  
  
## <a name="arguments"></a>引數  
`[ @principal_id = ] principal_id` 這是要列出之關聯的 **msdb** 資料庫中，資料庫使用者或角色的識別碼。 *principal_id* 是 **int**，預設值是 Null。 可以指定 *principal_id* 或 *principal_name* 。  
  
`[ @principal_name = ] 'principal_name'` 這是要列出之關聯的 **msdb** 資料庫中，資料庫使用者或角色的名稱。 *principal_name* 是 **sysname**，預設值是 Null。 可以指定 *principal_id* 或 *principal_name* 。  
  
`[ @profile_id = ] profile_id` 這是要列出之關聯的設定檔識別碼。 *profile_id* 是 **int**，預設值是 Null。 可以指定 *profile_id* 或 *profile_name* 。  
  
`[ @profile_name = ] 'profile_name'` 這是要列出之關聯的設定檔名稱。 *profile_name* 是 **sysname**，預設值是 Null。 可以指定 *profile_id* 或 *profile_name* 。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="result-sets"></a>結果集  
 傳回包含下表所列資料行的結果集。  
  
| 資料行名稱 | 資料類型 | 描述 |
| ----------- | --------- | ----------- |
|**principal_id**|**int**|資料庫使用者的識別碼。|  
|**principal_name**|**sysname**|資料庫使用者的名稱。|  
|**profile_id**|**int**|Database Mail 設定檔的識別碼。|  
|**profile_name**|**sysname**|Database Mail 設定檔的名稱。|  
|**is_default**|**bit**|指出設定檔是否為使用者預設設定檔的旗標。|  
  
## <a name="remarks"></a>備註  
 如果叫用不含參數的 **sysmail_help_principalprofile_sp** ，傳回的結果集會列出實例中的所有關聯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 否則，結果集會包含符合提供參數之關聯的資訊。 例如，提供設定檔名稱時，程序便會列出設定檔的所有關聯。  
  
 **sysmail_help_principalprofile_sp** 位於 **msdb** 資料庫中，而且是由 **dbo** 架構所擁有。 如果目前的資料庫不是 **msdb**，就必須以三部分名稱執行程式。  
  
## <a name="permissions"></a>權限  
 需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-listing-information-for-a-specific-association"></a>A. 列出特定關聯的資訊  
 下列範例會顯示 `AdventureWorks Administrator` 設定檔和 `ApplicationLogin` 資料庫中的 `msdb` 主體間之所有關聯的資訊。  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp  
    @principal_name = 'danw',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 範例結果集如下 (行的長度經過重新格式化)。  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
5            danw               9           AdventureWorks Administrator   1  
```  
  
### <a name="b-listing-information-for-all-associations"></a>B. 列出所有關聯的資訊  
 下列範例會顯示如何列出執行個體中之所有關聯的資訊。  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp ;  
```  
  
 範例結果集如下 (行的長度經過重新格式化)。  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
6            terrid             3           Product Update Profile         1  
5            danw               9           AdventureWorks Administrator   1  
```  
  
## <a name="see-also"></a>另請參閱  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [&#40;Transact-sql&#41;的 Database Mail 預存程式 ](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
