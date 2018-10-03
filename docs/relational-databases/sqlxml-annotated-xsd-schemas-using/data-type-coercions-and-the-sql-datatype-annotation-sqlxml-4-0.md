---
title: '資料類型強制型轉和 sql: datatype 註解 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7deb5fc8da17c597b22cb4e2e3e689191de2533b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842436"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a>資料類型強制型轉和 sql:datatype 註解 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  在 XSD 結構描述**xsd: type**屬性會指定元素或屬性的 XSD 資料型別。 當 XSD 結構描述用於從資料庫擷取資料時，指定的資料類型則會用於將資料格式化。  
  
 除了指定 XSD 類型的結構描述中，您也可以指定 Microsoft[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用的資料型別**sql: datatype**註釋。 **Xsd: type**並**sql: datatype**屬性會控制 XSD 資料型別之間的對應和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料型別。  
  
## <a name="xsdtype-attribute"></a>xsd:type 屬性  
 您可以使用**xsd: type**屬性來指定屬性或項目會對應至資料行的 XML 資料類型。 **Xsd: type**會影響從伺服器以及執行的 XPath 查詢傳回的文件。 針對對應結構描述，其中包含執行 XPath 查詢時**xsd: type**，處理查詢時，XPath 會使用指定的資料類型。 如需有關如何使用 XPath **xsd: type**，請參閱[對應 XSD 資料型別以 XPath 資料型別&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md)。  
  
 在傳回的文件中，所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型會轉換為字串表示。 某些資料類型需要額外的轉換。 下表列出可用於各種轉換**xsd: type**值。  
  
|XSD 資料類型|SQL Server 轉換|  
|-------------------|---------------------------|  
|布林|CONVERT(bit, COLUMN)|  
|date|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|Decimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|Time|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|All others|No additional conversion|  
  
> [!NOTE]  
>  所傳回之值的一些[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可能無法使用所指定的 XML 資料類型相容**xsd: type**，這是因為不可能轉換 (比方說，將"XYZ"轉換成**十進位**資料類型) 或是因為值超過該資料類型的範圍 (例如，-100000 轉換成**UnsignedShort** XSD 型別)。 不相容的類型轉換可能產生無效的 XML 文件或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤。  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>從 SQL Server 資料類型對應到 XSD 資料類型  
 下表列出從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型對應到 XSD 資料類型的明顯對應。 如果您知道 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型，這個表格會提供您在 XSD 結構描述中可以指定的對應 XSD 類型。  
  
|SQL Server 資料類型|XSD 資料類型|  
|--------------------------|-------------------|  
|**bigint**|**長**|  
|**binary**|**base64Binary**|  
|**bit**|**boolean**|  
|**char**|**string**|  
|**datetime**|**dateTime**|  
|**decimal**|**decimal**|  
|**float**|**double**|  
|**image**|**base64Binary**|  
|**int**|**int**|  
|**money**|**decimal**|  
|**nchar**|**string**|  
|**ntext**|**string**|  
|**nvarchar**|**string**|  
|**numeric**|**decimal**|  
|**real**|**float**|  
|**smalldatetime**|**dateTime**|  
|**smallint**|**short**|  
|**smallmoney**|**decimal**|  
|**sql_variant**|**string**|  
|**sysname**|**string**|  
|**text**|**string**|  
|**timestamp**|**dateTime**|  
|**tinyint**|**unsignedByte**|  
|**varbinary**|**base64Binary**|  
|**varchar**|**string**|  
|**uniqueidentifier**|**string**|  
  
## <a name="sqldatatype-annotation"></a>sql:datatype 註解  
 **Sql: datatype**註解用來指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料類型，而且此註解時，必須指定：  
  
-   您是大量載入到**dateTime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料行，從 XSD **dateTime**，**日期**，或**時間**型別。 在此情況下，您必須找出[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用的資料行資料類型**sql: datatype ="dateTime"**。 這項規則也套用於 Updategram。  
  
-   您要大量載入的資料行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **uniqueidentifier**型別，而且 XSD 值是 GUID，包含大括號 （{和}）。 當您指定**sql: datatype ="uniqueidentifier"** 之前它會插入資料行中,，將會移除值的大括號。 如果**sql: datatype**未指定，則傳送值大括號，與在 insert 或 update 將失敗。  
  
-   XML 資料型別**base64Binary**對應到各種[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料類型 (**二進位**，**映像**，或**varbinary**)。 若要將 XML 資料類型對應**base64Binary**特定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料類型，請使用**sql: datatype**註釋。 該註解會指定資料行明確的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，而該資料行是屬性對應之資料行。 當資料儲存在資料庫中時，這樣的作法就很有用。 藉由指定**sql: datatype**註解，您可以識別明確[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料型別。  
  
 通常建議您指定**sql: datatype**結構描述中。  
  
## <a name="examples"></a>範例  
 若要使用下列範例建立工作範例，您必須符合某些需求。 如需詳細資訊，請參閱 <<c0> [ 如需執行 SQLXML 範例的需求](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)。  
  
### <a name="a-specifying-xsdtype"></a>A. 指定 xsd:type  
 此範例會示範如何 XSD**日期**使用指定的型別**xsd: type**結構描述中的屬性會影響產生的 XML 文件。 該結構描述在 AdventureWorks 資料庫中會提供 Sales.SalesOrderHeader 資料表的 XML 檢視。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 在這個 XSD 結構描述中，有三種屬性會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回日期值。 當結構描述：  
  
-   指定**xsd: type = 日期**上**OrderDate**屬性時，所傳回的值的日期部分[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如**OrderDate**就會顯示屬性。  
  
-   指定**xsd: type = 時間**上**ShipDate**屬性時，所傳回的值時間部分[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如**ShipDate**就會顯示屬性。  
  
-   未指定**xsd: type**上**DueDate**屬性，就會有相同的值，由[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]隨即出現。  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>針對結構描述測試範例 XPath 查詢  
  
1.  複製上述的結構描述程式碼，並將其貼到文字檔中。 將檔案儲存為 xsdType.xml。  
  
2.  複製下列範本，並將其貼到文字檔中。 將檔案儲存為 xsdTypeT.xml 並放在與 xsdType.xml 一樣的目錄中。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     指定給對應結構描述 (xsdType.xml) 的目錄路徑，與儲存範本之目錄相關。 您也可以指定絕對路徑，例如：  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。  
  
     如需詳細資訊，請參閱 <<c0> [ 使用 ADO 執行 SQLXML 4.0 查詢](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
 部分結果集如下：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 這是相等的 XDR 結構描述：  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a>B. 藉由使用 sql:datatype 指定 SQL 資料類型  
 如需實用範例，請參閱中的範例 G [XML 大量載入範例&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)。 在這個範例中，包含 "{" 和 "}" 的 GUID 值是大量載入的。 在此範例中的結構描述指定**sql: datatype**識別[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料類型作為**uniqueidentifier**。 此範例會說明何時**sql: datatype**必須指定結構描述中。  
  
  
