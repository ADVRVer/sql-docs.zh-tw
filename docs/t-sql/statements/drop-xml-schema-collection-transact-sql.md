---
title: DROP XML SCHEMA COLLECTION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP XML SCHEMA COLLECTION
- DROP_XML_SCHEMA_COLLECTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting XML schema collections
- XML schema collections [SQL Server], removing
- schema collections [SQL Server], removing
- removing XML schema collections
- dropping XML schema collections
- DROP XML SCHEMA COLLECTION statement
ms.assetid: d686f2f5-e03a-4ffe-a566-6036628f46f1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 320c11c78f95f644e373b1cd410858a81e72edad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804486"
---
# <a name="drop-xml-schema-collection-transact-sql"></a>DROP XML SCHEMA COLLECTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  刪除整個 XML 結構描述集合及其所有的元件。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
DROP XML SCHEMA COLLECTION [ relational_schema. ]sql_identifier  
```  
  
## <a name="arguments"></a>引數  
 *relational_schema*  
 識別關聯式結構描述名稱。 若未指定，則會假設使用預設的關聯式結構描述。  
  
 *sql_identifier*  
 這是您要卸除的 XML 結構描述集合名稱。  
  
## <a name="remarks"></a>Remarks  
 卸除 XML 結構描述集合是一項交易式作業。 也就是說，當您卸除交易內的 XML 結構描述集合，然後再回復該交易時，不會卸除 XML 結構描述集合。  
  
 您不能卸除在使用中的 XML 結構描述集合。 也就是說，下列幾種集合不能卸除：  
  
-   與任何 **xml** 類型參數或資料行相關聯的集合。  
  
-   在任何資料表條件約束中指定的集合。  
  
-   在結構描述繫結函數或預存程序中參考的集合。 例如，下列函數會鎖定 XML 結構描述集合 `MyCollection`，因為該函數會指定 `WITH SCHEMABINDING`。 如果移除它，XML SCHEMA COLLECTION 就沒有任何鎖定。  
  
    ```  
    CREATE FUNCTION dbo.MyFunction()  
    RETURNS int  
    WITH SCHEMABINDING  
    AS  
    BEGIN  
       ...  
       DECLARE @x XML(MyCollection)  
       ...  
    END;  
    ```  
  
## <a name="permissions"></a>[權限]  
 若要卸除 XML SCHEMA COLLECTION，則需要集合的 DROP 權限。  
  
## <a name="examples"></a>範例  
 下列範例會顯示移除 XML 結構描述集合。  
  
```  
DROP XML SCHEMA COLLECTION ManuInstructionsSchemaCollection;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [ALTER XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [比較具類型的 XML 與不具類型的 XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [伺服器上 XML 結構描述集合的需求與限制](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
