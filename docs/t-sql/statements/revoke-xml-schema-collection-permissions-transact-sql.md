---
title: "撤銷 XML 結構描述集合權限 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statement, XML schema collections
- XML schema collections [SQL Server], permissions
- schema collections [SQL Server], permissions
ms.assetid: 8ca0973c-30b2-4633-a165-c09b13cc81ae
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4d7d530e89bdd3dcb320c4a08c340071b7faba3
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-xml-schema-collection-permissions-transact-sql"></a>REVOKE XML 結構描述集合權限 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  撤銷授與或拒絕的 XML 結構描述集合權限。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ] ON   
    XML SCHEMA COLLECTION :: [ schema_name . ]  
    XML_schema_collection_name  
    { TO | FROM } <database_principal> [ ,...n ]  
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
 *權限*  
 指定可以撤銷的 XML 結構描述集合權限。 如需權限清單，請參閱這個主題稍後的「備註」一節。  
  
 在 XML 結構描述集合:: [ *schema_name***。** ] *XML_schema_collection_name*  
 指定要撤銷其權限的 XML 結構描述集合。 需要範圍限定詞 (::)。 如果*schema_name*未指定，會使用預設的結構描述。 如果*schema_name*指定，則是必要的結構描述範圍限定詞 （.）。  
  
 GRANT OPTION  
 指出會撤銷對其他主體授與指定權限的權限。 不會撤銷權限本身。  
  
> [!IMPORTANT]  
>  如果主體有不含 GRANT 選項的指定權限，則會撤銷權限本身。  
  
 CASCADE  
 指出目前正在撤銷的權限，而這個權限也會被這個主體所授與或拒絕的其他主體所撤銷。  
  
> [!CAUTION]  
>  獲得授與 WITH GRANT OPTION 之權限的串聯撤銷，會同時撤銷該權限的 GRANT 和 DENY。  
  
 {至 |FROM} \< *database_principal*>  
 指定要撤銷其權限的主體。  
  
 AS \<database_principal > 指定要從中執行此查詢的主體衍生權限來撤銷權限的主體。  
  
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
 XML 結構描述集合的資訊會顯示在[sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md)目錄檢視。  
  
 從被授與指定了 GRANT OPTION 之權限的主體撤銷權限時，如果未指定 CASCADE，陳述式便會失敗。  
  
 XML 結構描述集合是一個由結構描述所包含的結構描述層級安全性實體，在權限階層中，此結構描述為該安全性實體的父系。 下表所列的是可以撤銷之最特定且最有限的 XML 結構描述集合權限，並列出利用隱含方式來併入這些權限的較通用權限。  
  
|XML 結構描述集合權限|XML 結構描述集合所隱含|結構描述權限所隱含|  
|--------------------------------------|-------------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|執行 CREATE 陳述式之前，請先執行|CONTROL|執行 CREATE 陳述式之前，請先執行|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 需要 XML 結構描述集合的 CONTROL 權限。 如果使用 AS 選項，指定的主體必須擁有 XML 結構描述集合。  
  
## <a name="examples"></a>範例  
 下列範例會從使用者 `EXECUTE` 撤銷 XML 結構描述集合 `Invoices4` 的 `Wanida` 權限。 XML 結構描述集合 `Invoices4` 在 `Sales` 資料庫中 `AdventureWorks2012` 結構描述內。  
  
 ```
 USE AdventureWorks2012;  
 REVOKE EXECUTE ON XML SCHEMA COLLECTION::Sales.Invoices4 FROM Wanida;  
 GO
 ```  
  
## <a name="see-also"></a>另請參閱  
 [授與 XML 結構描述集合權限 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)   
 [拒絕 XML 結構描述集合權限 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/deny-xml-schema-collection-permissions-transact-sql.md)   
 [sys.xml_schema_collections &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md)   
 [建立 XML 結構描述集合 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [權限 &#40;資料庫引擎&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


