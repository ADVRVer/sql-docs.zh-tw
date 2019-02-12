---
title: 用戶端和伺服器端 XML 格式化 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- FOR XML clause, formatting
- client-side XML formatting
- server-side XPath
- server-side XML formatting
- AUTO mode
- client-side XPath
ms.assetid: f807ab7a-c5f8-4e61-9b00-23aebfabc47e
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cd9f76b11edf684c68658f040b4aa3e0f63727d4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2019
ms.locfileid: "56028829"
---
# <a name="client-side-vs-server-side-xml-formatting-sqlxml-40"></a>用戶端和伺服器端 XML 格式 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  本主題描述 SQLXML 中用戶端與伺服器端 XML 格式化之間的一般差異。  
  
## <a name="multiple-rowset-queries-not-supported-in-client-side-formatting"></a>用戶端格式中不支援多個資料列集查詢  
 當您使用用戶端 XML 格式化時，不支援會產生多個資料列集的查詢。 例如，假設您有一個虛擬目錄，您已在其中指定用戶端格式。 請考慮這個範例範本，有兩個 SELECT 陳述式中 **\<sql:query >** 區塊：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
     SELECT FirstName FROM Person.Contact FOR XML Nested;   
     SELECT LastName FROM Person.Contact FOR XML Nested    
  </sql:query>  
</ROOT>  
```  
  
 您可以在應用程式的程式碼中執行這個範本，而且會傳回錯誤，因為用戶端 XML 格式化不支援多個資料列集的格式。 如果您指定查詢在兩個分隔 **\<sql:query >** 區塊，您會想要的結果。  
  
## <a name="timestamp-maps-differently-in-client--vs-server-side-formatting"></a>時間戳記在用戶端與伺服器端格式中的對應不同  
 在 伺服器端 XML 格式化中，資料庫資料行會**時間戳記**類型會對應到 i8 XDR 類型 （當在查詢中指定 XMLDATA 選項）。  
  
 在用戶端 XML 格式化中，資料庫資料行**時間戳記**類型會對應至其中一個**uri**或**bin.hex、bin.base64** XDR 類型 (取決於是否 binary base64選項會指定在查詢中）。 **Bin.hex、bin.base64** XDR 類型會非常有用，如果您要使用 updategram 和大量載入功能，因為此類型會轉換成[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**時間戳記**型別。 如此一來，插入、更新或刪除作業都會成功。  
  
## <a name="deep-variants-are-used-in-server-side-formatting"></a>伺服器端格式中會使用深入的 VARIANT  
 在伺服器端 XML 格式化中，會使用深入類型的 VARIANT 類型。 如果您使用用戶端 XML 格式化，Variant 會轉換成 Unicode 字串，而且不會使用 VARIANT 的子類型。  
  
## <a name="nested-mode-vs-auto-mode"></a>NESTED 模式與AUTO 模式的比較  
 用戶端 FOR XML 的 NESTED 模式類似於伺服器端 FOR XML 的 AUTO 模式，但是以下情況除外：  
  
### <a name="when-you-query-views-using-auto-mode-on-the-server-side-the-view-name-is-returned-as-the-element-name-in-the-resulting-xml"></a>當您在伺服器端上使用 AUTO 模式來查詢檢視表時，檢視表名稱會當做產生之 XML 中的元素名稱傳回。  
 例如，假設 AdventureWorksdatabase 中的 Person.Contact 資料表上，建立下列檢視：  
  
```  
CREATE VIEW ContactView AS (SELECT ContactID as CID,  
                               FirstName  as FName,  
                               LastName  as LName  
                        FROM Person.Contact)  
```  
  
 下列範本會針對 ContactView 檢視表指定一個查詢，也會指定伺服器端 XML 格式化：  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT *  
    FROM   ContactView  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 當您執行此範本時，將會傳回下列 XML  (只會顯示部分結果)。請注意，元素名稱是此查詢執行時所針對的檢視表名稱。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ContactView CID="1" FName="Gustavo" LName="Achong" />   
  <ContactView CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
 當您使用對應的 NESTED 模式指定用戶端 XML 格式化時，基底資料表名稱會當做產生之 XML 中的元素名稱傳回。 例如，下列修改過的範本執行相同的 SELECT 陳述式，但 XML 格式化時，會對用戶端 (亦即**用戶端端 xml**設為範本中，則為 true):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT *  
    FROM   ContactView  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 執行這個範本會產生以下 XML。 請注意，此案例中的元素名稱是基底資料表名稱。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact CID="1" FName="Gustavo" LName="Achong" />   
  <Person.Contact CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
### <a name="when-you-use-auto-mode-of-the-server-side-for-xml-the-table-aliases-specified-in-the-query-are-returned-as-element-names-in-the-resulting-xml"></a>當您使用伺服器端 FOR XML 的 AUTO 模式時，查詢中所指定的資料表別名會當做產生之 XML 中的元素名稱傳回。  
 例如，假設有以下的範本：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 執行此範本會產生以下 XML：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <C fname="Gustavo" lname="Achong" />   
  <C fname="Catherine" lname="Abel" />   
...  
</ROOT>   
```  
  
 當您使用用戶端 FOR XML 的 NESTED 模式時，資料表名稱會當做產生之 XML 中的元素名稱傳回  (將不會使用查詢中指定的資料表別名)。例如，假設有以下的範本：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 執行此範本會產生以下 XML：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact fname="Gustavo" lname="Achong" />   
  <Person.Contact fname="Catherine" lname="Abel" />   
...  
</ROOT>  
```  
  
### <a name="if-you-have-a-query-that-returns-columns-as-dbobject-queries-you-cannot-use-aliases-for-these-columns"></a>如果您的查詢將資料行當做 dbobject 查詢傳回，您將無法針對這些資料行使用別名。  
 例如，假設有以下的範本，此範本所執行的查詢會傳回員工識別碼和相片。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query client-side-xml="1">  
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML NESTED, elements  
</sql:query>  
</ROOT>  
```  
  
 執行這個範本會將 Photo 資料行當做 dbobject 查詢傳回。 在此 dbobject 查詢中，`@P` 會參考不存在的資料行名稱。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@P</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
 如果 XML 格式化在伺服器上完成 (**用戶端端 xml ="0"**)，您可以用於傳回 dbobject 查詢在實際的資料表和資料行 （即使您有指定的別名），會傳回名稱的資料行中的別名。 例如，下列範本會執行查詢，而 XML 格式化在伺服器上完成 (**用戶端端 xml**未指定選項和**Run On Client**選項未選取虛擬根目錄）。 此查詢也會指定 AUTO 模式 (而非用戶端 NESTED 模式)。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query   
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML AUTO, elements  
</sql:query>  
</ROOT>  
```  
  
 當執行這個範本時，將會傳回下列 XML 文件 (請注意，LargePhoto 資料行的 dbobject 查詢中不會使用別名)。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@LargePhoto</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
### <a name="client-side-vs-server-side-xpath"></a>用戶端和伺服器端的 XPath  
 用戶端 XPath 和伺服器端 XPath 的運作方式相同，但是有下列幾項差異：  
  
-   當您使用用戶端 XPath 查詢時所套用的資料轉換與使用伺服器端 XPath 查詢時所套用的資料轉換不同。 用戶端 XPath 會使用 CAST，而非 CONVERT 模式 126。  
  
-   當您指定**用戶端端 xml ="0"** (false) 在範本中，您會要求伺服器端 XML 格式化。 因此，您無法指定 FOR XML NESTED，因為伺服器無法辨識 NESTED 選項。 這樣會產生錯誤。 您必須使用伺服器可辨識的 AUTO、RAW 或 EXPLICIT 模式。  
  
-   當您指定**用戶端端 xml ="1"** (true) 在範本中，您會要求用戶端 XML 格式化。 在此情況下，您可以指定 FOR XML NESTED。 如果您指定 FOR XML AUTO，XML 格式化，就會發生在伺服器端雖然**用戶端端 xml ="1"** 範本中所指定。  
  
## <a name="see-also"></a>另請參閱  
 [FOR XML 安全性考量&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md)   
 [用戶端 XML 格式化&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)   
 [伺服器端 XML 格式化&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/server-side-xml-formatting-sqlxml-4-0.md)  
  
  
