---
description: sp_changedbowner (Transact-SQL)
title: sp_changedbowner (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_changedbowner
- sp_changedbowner_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changedbowner
ms.assetid: 516ef311-e83b-45c9-b9cd-0e0641774c04
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dc4f29dba1a922b5adae32e0fc42cf714afc292f
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753480"
---
# <a name="sp_changedbowner-transact-sql"></a>sp_changedbowner (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  變更目前資料庫的擁有者。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 改為使用 [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_changedbowner [ @loginame = ] 'login'  
     [ , [ @map = ] remap_alias_flag ]  
```  
  
## <a name="arguments"></a>引數  
 [ @loginame =] '*login*'  
 這是目前資料庫新擁有者的登入識別碼。 *login* 是 **sysname**，沒有預設值。 *登* 入必須是已經存在的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入或 Windows 使用者。 如果*登*入已經透過資料庫中現有的使用者安全性帳戶來存取資料庫，就不能成為目前資料庫的擁有者。 若要防止這種情況，請先卸除目前資料庫的使用者。  
  
 [ @map =] *remap_alias_flag*  
 *Remap_alias_flag*的參數已被取代，因為已從移除登入別名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 使用 *remap_alias_flag* 參數並不會造成錯誤，但也不會有任何作用。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 在 sp_changedbowner 執行之後，新擁有者在資料庫中就成為 dbo 使用者。 dbo 具有隱含權限，可以執行資料庫中所有的活動。  
  
 master、model 或 tempdb 系統資料庫的擁有者不能變更。  
  
 若要顯示有效 *登* 入值的清單，請執行 sp_helplogins 預存程式。  
  
 只要使用 *login* 參數執行 sp_changedbowner，就會將資料庫擁有權變更為 *登*入。  
  
 不過，您也可以利用 ALTER AUTHORIZATION 陳述式來變更任何安全性實體的擁有者。 如需詳細資訊，請參閱 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)。  
  
## <a name="permissions"></a>權限  
 需要資料庫的 TAKE OWNERSHIP 權限。 如果新擁有者在資料庫有對應的使用者，則需要登入的 IMPERSONATE 權限，否則就需要伺服器的 CONTROL SERVER 權限。  
  
## <a name="examples"></a>範例  
 下列範例會讓登入 `Albert` 成為目前資料庫的擁有者。  
  
```  
EXEC sp_changedbowner 'Albert';  
```  
  
## <a name="see-also"></a>另請參閱  
 [安全性預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md)   
 [sp_dropalias &#40;Transact-sql&#41;](./system-stored-procedures-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helpdb &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helplogins &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
