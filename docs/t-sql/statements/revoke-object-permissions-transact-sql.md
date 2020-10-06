---
description: REVOKE 物件權限 (Transact-SQL)
title: REVOKE 物件權限 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table permissions [SQL Server], revoking
- REVOKE statement, objects
- revoking permissions to access tables
- object permissions [SQL Server], revoking
ms.assetid: 99c7146e-d2e7-4f1a-80ff-21a05bc5e8bb
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 192eb99c7ba6e4472faee82aa3b3636b35423478
ms.sourcegitcommit: b93beb4f03aee2c1971909cb1d15f79cd479a35c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91497748"
---
# <a name="revoke-object-permissions-transact-sql"></a>REVOKE 物件權限 (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  撤銷資料表、檢視表、資料表值函式、預存程序、擴充預存程序、純量函數、彙總函式、服務佇列或同義字的權限。 
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```syntaxsql
REVOKE [ GRANT OPTION FOR ] <permission> [ ,...n ] ON   
    [ OBJECT :: ][ schema_name ]. object_name [ ( column [ ,...n ] ) ]  
        { FROM | TO } <database_principal> [ ,...n ]   
    [ CASCADE ]  
    [ AS <database_principal> ]  
  
<permission> ::=  
    ALL [ PRIVILEGES ] | permission [ ( column [ ,...n ] ) ]  
  
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
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>引數
 *permission*  
 指定可以撤銷的結構描述所含物件之權限。 如需權限清單，請參閱這個主題稍後的「備註」一節。  
  
 ALL  
 撤銷 ALL 不會撤銷所有可能的權限。 撤銷 ALL 相當於撤銷所有適用於指定物件的 [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]-92 權限。 ALL 有多種意義，如下所示：  
  
 純量函式權限：EXECUTE、REFERENCES。  
  
 資料表值函式權限：DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
 預存程序權限：EXECUTE。  
  
 資料表權限：DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
 檢視權限：DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
 PRIVILEGES  
 為符合 [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]-92 而包含這個項目。 不會變更 ALL 的行為。  
  
 *column*  
 在撤銷其權限之資料表、檢視或資料表值函式中指定資料行名稱。 必須以括弧 ( ) 括住。 只能拒絕資料行的 SELECT、REFERENCES 及 UPDATE 權限。 *column* 可以在權限子句中或在安全性實體名稱之後指定 。  
  
 ON [ OBJECT :: ] [ *schema_name* ] . *object_name*  
 指定要撤銷其權限的物件。 若指定 *schema_name*，則 OBJECT 片語為選擇性。 如果使用 OBJECT 片語，則需要範圍限定詞 (::)。 若未指定 *schema_name*，則會使用預設結構描述。 若指定 *schema_name*，則結構描述範圍限定詞 (.) 是必要項目。  
  
 { FROM | TO } \<database_principal> 指定要撤銷其權限的主體。  
  
 GRANT OPTION  
 指出會撤銷對其他主體授與指定權限的權限。 不會撤銷權限本身。  
  
> [!IMPORTANT]  
>  如果主體有不含 GRANT 選項的指定權限，則會撤銷權限本身。  
  
 CASCADE  
 指出目前正在撤銷的權限，而這個權限也會被這個主體所授與或拒絕的其他主體所撤銷。  
  
> [!CAUTION]  
>  獲得授與 WITH GRANT OPTION 之權限的串聯撤銷，會同時撤銷該權限的 GRANT 和 DENY。  
  
 AS \<database_principal> 指定主體，執行這項查詢的主體會從這個主體衍生權利來撤銷權限。  
  
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
  
## <a name="remarks"></a>備註  
 可以在各種目錄檢視中看到物件的相關資訊。 如需詳細資訊，請參閱[物件目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)。  
  
 物件是一個由結構描述所包含的結構描述層級安全性實體，在權限階層中，此結構描述為該安全性實體的父系。 下表所列的是可以撤銷之最特定且最有限的物件權限，並列出利用隱含方式來併入這些權限的較通用權限。  
  
|物件權限|物件權限所隱含|結構描述權限所隱含|  
|-----------------------|----------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|刪除|CONTROL|刪除|  
|執行 CREATE 陳述式之前，請先執行|CONTROL|執行 CREATE 陳述式之前，請先執行|  
|Insert|CONTROL|Insert|  
|RECEIVE|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|RECEIVE|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|VIEW CHANGE TRACKING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>權限  
 需要物件的 CONTROL 權限。  
  
 如果使用 AS 子句，指定的主體必須擁有要撤銷其權限的物件。  
  
## <a name="examples"></a>範例  
  
### <a name="a-revoking-select-permission-on-a-table"></a>A. 撤銷資料表的 SELECT 權限  
 下列範例會從使用者 `SELECT` 撤銷 `RosaQdM` 資料庫中之資料表 `Person.Address` 的 `AdventureWorks2012` 權限。  
  
```sql  
USE AdventureWorks2012;  
REVOKE SELECT ON OBJECT::Person.Address FROM RosaQdM;  
GO  
```  
  
### <a name="b-revoking-execute-permission-on-a-stored-procedure"></a>B. 撤銷預存程序的 EXECUTE 權限  
 下列範例會對一個稱為 `EXECUTE` 的應用程式角色，撤銷預存程序 `HumanResources.uspUpdateEmployeeHireInfo` 的 `Recruiting11` 權限。  
  
```sql  
USE AdventureWorks2012;  
REVOKE EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    FROM Recruiting11;  
GO   
```  
  
### <a name="c-revoking-references-permission-on-a-view-with-cascade"></a>C. 撤銷具有 CASCADE 之檢視的 REFERENCES 權限  
 下列範例會從具有 `REFERENCES` 之使用者 `BusinessEntityID` 撤銷檢視 `HumanResources.vEmployee` 中之資料行 `Wanida` 的 `CASCADE` 權限。  
  
```sql  
USE AdventureWorks2012;  
REVOKE REFERENCES (BusinessEntityID) ON OBJECT::HumanResources.vEmployee   
    FROM Wanida CASCADE;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [GRANT 物件權限 &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [DENY 物件權限 &#40;Transact-SQL&#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)   
 [物件目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [權限 &#40;資料庫引擎&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [安全性實體](../../relational-databases/security/securables.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [sys.fn_my_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)  
  
  

