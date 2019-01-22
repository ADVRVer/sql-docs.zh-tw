---
title: DENY 類型權限 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- DENY statement, types
- permissions [SQL Server], types
- type permissions [SQL Server]
- denying permissions [SQL Server], types
ms.assetid: 564e3500-c567-43dc-993b-9ab50e99cf3f
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 280d5d37ca364e32e2bd8638cdd03563a2b86f49
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361493"
---
# <a name="deny-type-permissions-transact-sql"></a>DENY 類型權限 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  拒絕 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中類型的權限。  

 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
DENY permission  [ ,...n ] ON TYPE :: [ schema_name . ] type_name  
        TO <database_principal> [ ,...n ]  
    [ CASCADE ]  
    [ AS <database_principal> ]  
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login  
```  
  
## <a name="arguments"></a>引數  
 *permission*  
 指定可以拒絕的類型權限。 如需權限清單，請參閱這個主題稍後的「備註」一節。  
  
 ON TYPE **::** [ _schema_name_**.** ] *type_name*  
 指定要拒絕其權限的類型。 範圍限定詞 (**::**) 是必要項。 如果未指定 *schema_name*，則使用預設結構描述。 如果指定 *schema_name*，則結構描述範圍限定詞 (**.**) 為必要項目。  
  
 TO \<database_principal>  
 指定要拒絕其權限的主體。  
  
 CASCADE  
 指出目前受到拒絕的權限，也為這個主體曾授與此權限的其他主體所拒絕。  
  
 AS \<database_principal>  
 指定主體，執行這項查詢的主體會從這個主體衍生權限來拒絕權限。  
  
 *Database_user*  
 指定資料庫使用者。  
  
 *Database_role*  
 指定資料庫角色。  
  
 *Application_role*  
   
 指定應用程式角色。  
  
 *Database_user_mapped_to_Windows_User*  
 
 指定對應至 Windows 使用者的資料庫使用者。  
  
 *Database_user_mapped_to_Windows_Group*  
 
 指定對應至 Windows 群組的資料庫使用者。  
  
 *Database_user_mapped_to_certificate*  
 
 指定對應至憑證的資料庫使用者。  
  
 *Database_user_mapped_to_asymmetric_key*  
  
 指定對應至非對稱金鑰的資料庫使用者。  
  
 *Database_user_with_no_login*  
 指定不含對應伺服器層級主體的資料庫使用者。  
  
## <a name="remarks"></a>Remarks  
 類型是一個由結構描述所包含的結構描述層級安全性實體，在權限階層中，此結構描述為該安全性實體的父系。  
  
> [!IMPORTANT]  
>  **GRANT**、**DENY** 和 **REVOKE** 權限不適用於系統類型。 使用者定義類型可以被授與權限。 如需使用者定義型別的詳細資訊，請參閱[在 SQL Server 中使用使用者定義型別](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)。  
  
 下表所列的是可以拒絕之最特定且最有限的類型權限，並列出利用隱含方式來併入這些權限的較通用權限。  
  
|類型權限|類型權限所隱含|結構描述權限所隱含|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|執行 CREATE 陳述式之前，請先執行|CONTROL|執行 CREATE 陳述式之前，請先執行|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>[權限]  
 需要類型的 CONTROL 權限。 如果使用 AS 子句，指定的主體必須擁有要拒絕其權限的類型。  
  
## <a name="examples"></a>範例  
 下列範例會對 `VIEW DEFINITION` 拒絕使用者定義類型 `CASCADE` 之具有 `PhoneNumber` 的 `KhalidR` 權限。 `PhoneNumber` 位於結構描述 `Telemarketing`。  
  
```  
DENY VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    TO KhalidR CASCADE;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [GRANT 類型權限 &#40;Transact-SQL&#41;](../../t-sql/statements/grant-type-permissions-transact-sql.md)   
 [REVOKE 類型權限 &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-type-permissions-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [權限 &#40;資料庫引擎&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [安全性實體](../../relational-databases/security/securables.md)  
  
  
