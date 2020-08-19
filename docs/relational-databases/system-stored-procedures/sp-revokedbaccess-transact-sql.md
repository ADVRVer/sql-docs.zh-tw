---
description: sp_revokedbaccess (Transact-SQL)
title: sp_revokedbaccess (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokedbaccess_TSQL
- sp_revokedbaccess
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokedbaccess
ms.assetid: c997cfa1-539d-485c-a664-9c6f76bfe0c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: cd16821bcbac3c814a7b164fa16501bca7a8f523
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446777"
---
# <a name="sp_revokedbaccess-transact-sql"></a>sp_revokedbaccess (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  從目前資料庫移除資料庫使用者。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用 [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_revokedbaccess [ @name_in_db = ] 'name'  
```  
  
## <a name="arguments"></a>引數  
`[ @name_in_db = ] 'name'` 這是要移除之資料庫使用者的名稱。 *名稱* 是 **sysname** ，沒有預設值。 *名稱* 可以是伺服器登入、windows 登入或 windows 群組的名稱，且必須存在於目前的資料庫中。 當您指定 Windows 登入或 Windows 群組時，請指定它在資料庫中的識別名稱。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 當移除資料庫使用者時，也會移除相依於該使用者的權限和別名。  
  
 **sp_revokedbaccess** 只能移除目前資料庫中的資料庫使用者。 移除擁有目前資料庫中之物件的資料庫使用者之前，必須先從資料庫傳送物件的擁有權或卸除這些物件。 如需詳細資訊，請參閱 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)。  
  
 **sp_revokedbaccess** 無法在使用者自訂交易內執行。  
  
## <a name="permissions"></a>權限  
 需要資料庫的 ALTER ANY USER 權限。  
  
## <a name="examples"></a>範例  
 下列範例會 `Edmonds\LolanSo` 從目前資料庫中移除對應至的資料庫使用者。  
  
```  
EXEC sp_revokedbaccess 'Edmonds\LolanSo';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的安全性預存程式 ](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [&#40;Transact-sql&#41;的系統預存程式 ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [DROP USER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
