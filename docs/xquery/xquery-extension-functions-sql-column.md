---
title: ': column （) 函數 (XQuery) |Microsoft Docs'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sql:column function
- sql:column() function
ms.assetid: e8f67bdf-b489-49a9-9d0f-2069c1750467
author: rothja
ms.author: jroth
ms.openlocfilehash: df46abb8efdd5761797a599cf5a8cdebe02e5158
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946014"
---
# <a name="xquery-extension-functions---sqlcolumn"></a>XQuery 擴充函式 - sql:column()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  主題中所述[繫結關聯式資料在 XML](../t-sql/xml/binding-relational-data-inside-xml-data.md)，您可以使用**sql:column(()** 函式使用時[XML 資料類型方法](../t-sql/xml/xml-data-type-methods.md)来公開的關聯式值XQuery 內。  
  
 例如， [query （） 方法 （XML 資料類型）](../t-sql/xml/query-method-xml-data-type.md)用來指定對儲存在變數或資料行的 XML 執行個體的查詢**xml**型別。 有時，您可能會想要讓查詢使用另一個非 XML 資料行的值，以同時查詢關聯式資料與 XML 資料。 若要這樣做，您使用 **: column （)** 函式。  
  
 SQL 值將會對應到一個相對應的 XQuery 值，且其類型會是等同於相對應 SQL 類型的 XQuery 基底類型。  
  
## <a name="syntax"></a>語法  
  
```  
  
sql:column("columnName")  
```  
  
## <a name="remarks"></a>備註  
 請注意，參考中指定的資料行 **: column （)** XQuery 內的函式參考正在處理的資料列中的資料行。  
  
 在  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，您只能參考**xml**執行個體內容中的來源運算式的 XML DML 插入陳述式; 否則您不能參考類型的資料行**xml**或 CLR使用者定義型別。  
  
 **: Column （)** 函式不支援聯結作業。 可改為使用 APPLY 作業。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-sqlcolumn-to-retrieve-the-relational-value-inside-xml"></a>A. 使用 sql:column() 來擷取 XML 內的關聯式值  
 在建構 XML 時，下列範例說明如何擷取非 XML 關聯式資料行的值，以繫結 XML 與關聯式資料。  
  
 此查詢建構具有下列格式的 XML：  
  
```xml
<Product ProductID="771" ProductName="Mountain-100 Silver, 38" ProductPrice="3399.99" ProductModelID="19"   
  ProductModelName="Mountain 100" />  
```  
  
 請注意在建構 XML 中的下列項目：  
  
-   **ProductID**， **ProductName**，並**ProductPrice**屬性值從取得**產品**資料表。  
  
-   **ProductModelID**屬性值從擷取**ProductModel**資料表。  
  
-   若要讓查詢更有趣的是， **ProductModelName**屬性值取自**CatalogDescription**資料行**xml 型別**。 由於並非所有的產品型號都有儲存 XML 產品型號目錄資訊，因此 `if` 陳述式可用以擷取存在的值。  
  
    ```sql
    SELECT P.ProductID, CatalogDescription.query('  
    declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
           <Product   
               ProductID=       "{ sql:column("P.ProductID") }"  
               ProductName=     "{ sql:column("P.Name") }"  
               ProductPrice=    "{ sql:column("P.ListPrice") }"  
               ProductModelID= "{ sql:column("PM.ProductModelID") }" >  
               { if (not(empty(/pd:ProductDescription))) then  
                 attribute ProductModelName { /pd:ProductDescription[1]/@ProductModelName }  
                else   
                   ()  
    }  
            </Product>  
    ') as Result  
    FROM Production.ProductModel PM, Production.Product P  
    WHERE PM.ProductModelID = P.ProductModelID  
    AND   CatalogDescription is not NULL  
    ORDER By PM.ProductModelID  
    ```  
  
 請注意下列項目是從上一個查詢而來：  
  
-   因為值是從兩個不同的資料表擷取而來，所以 FROM 子句會指定兩個資料表。 WHERE 子句中的條件會篩選結果，並只擷取產品型號含有目錄描述的產品。  
  
-   **命名空間**中的關鍵字[XQuery 初構](../xquery/modules-and-prologs-xquery-prolog.md)定義 XML 命名空間前置詞"pd"，在查詢主體中使用。 請注意資料表別名 "P" 與 "PM" 是定義在查詢本身的 FROM 子句中。  
  
-   **: Column （)** 函式用來將 XML 內的非 XML 值。  
  
 以下是部份結果：  
  
```  
ProductID               Result  
-----------------------------------------------------------------  
771         <Product ProductID="771"                   ProductName="Mountain-100 Silver, 38"   
                  ProductPrice="3399.99" ProductModelID="19"   
                  ProductModelName="Mountain 100" />  
...  
```  
  
 下列查詢建構了包含產品特定資訊的 XML。 此資訊包含隸屬於特定產品型號 ProductModelID=19 的所有產品之 ProductID、ProductName、ProductPrice 以及 ProductModelName (如果有的話)。 接著會將 XML 指派給@x的變數 **xml** 型別。  
  
```sql
declare @x xml  
SELECT @x = CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       <Product   
           ProductID=       "{ sql:column("P.ProductID") }"  
           ProductName=     "{ sql:column("P.Name") }"  
           ProductPrice=    "{ sql:column("P.ListPrice") }"  
           ProductModelID= "{ sql:column("PM.ProductModelID") }" >  
           { if (not(empty(/pd:ProductDescription))) then  
             attribute ProductModelName { /pd:ProductDescription[1]/@ProductModelName }  
            else   
               ()  
}  
        </Product>  
')   
FROM Production.ProductModel PM, Production.Product P  
WHERE PM.ProductModelID = P.ProductModelID  
And P.ProductModelID = 19  
select @x  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server XQuery 擴充函式](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [比較具類型的 XML 與不具類型的 XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML 資料 &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [建立 XML 資料的執行個體](../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml 資料類型方法](../t-sql/xml/xml-data-type-methods.md)   
 [XML 資料修改語言 &#40;XML DML&#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
