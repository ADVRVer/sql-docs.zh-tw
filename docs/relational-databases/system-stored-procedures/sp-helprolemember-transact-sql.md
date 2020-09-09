---
description: sp_helprolemember (Transact-SQL)
title: sp_helprolemember (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helprolemember_TSQL
- sp_helprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprolemember
ms.assetid: 42797510-aa5d-4564-85ac-27418419af9c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bbfec9641e543b4774a8d8d6f7a288bd2fe23c8a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541699"
---
# <a name="sp_helprolemember-transact-sql"></a>sp_helprolemember (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  傳回目前資料庫中直屬角色成員的相關資訊。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helprolemember [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @rolename = ] ' role '` 這是目前資料庫中的角色名稱。 *role* 是 **sysname**，預設值是 Null。 *角色* 必須存在於目前的資料庫中。 如果未指定 *role* ，則會傳回包含目前資料庫中至少一個成員的所有角色。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**DbRole**|**sysname**|目前資料庫中角色的名稱。|  
|**名**|**sysname**|DbRole 成員的名稱 **。**|  
|**MemberSID**|**varbinary(85)**|**成員名稱**的安全識別碼。|  
  
## <a name="remarks"></a>備註  
 如果資料庫包含嵌套角色，則 **成員** 名稱可能是角色的名稱。 **sp_helprolemember** 不會顯示透過嵌套角色取得的成員資格。 例如，如果 User1 是 Role1 的成員，而且 Role1 是 Role2 的成員，`EXEC sp_helprolemember 'Role2'`; 將會傳回 Role1，而不是 Role1 的成員 (此範例中為 User1)。 若要傳回嵌套成員資格，您必須針對每個嵌套角色重複執行 **sp_helprolemember** 。  
  
 使用 **sp_helpsrvrolemember** 來顯示固定伺服器角色的成員。  
  
 使用 [IS_ROLEMEMBER &#40;transact-sql&#41;](../../t-sql/functions/is-rolemember-transact-sql.md) 來檢查指定使用者的角色成員資格。  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會顯示 `Sales` 角色的成員。  
  
```  
EXEC sp_helprolemember 'Sales';  
```  
  
## <a name="see-also"></a>另請參閱  
 [安全性預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helpsrvrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
