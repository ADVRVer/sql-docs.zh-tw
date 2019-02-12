---
title: '建立 Valid ID-IDREF-IDREFS 類型屬性-sql: prefix (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- annotated XSD schemas, ID type attribute
- IDREF type attribute [SQLXML]
- annotated XSD schemas, IDREFS type attribute
- ID type attribute [SQLXML]
- sql:prefix
- prefix annotation
- IDREF relationships [SQLXML]
- IDREFS type attribute [SQLXML]
- annotated XSD schemas, IDREF type attribute
- ID relationships [SQLXML]
ms.assetid: 1c7f77d3-81f3-4820-bb63-c4aaa4ea9aa1
author: MightyPen
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 90b24662ab7e681cd2b762220556500da4a0d8a6
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2019
ms.locfileid: "56033009"
---
# <a name="creating-valid-id-idref-and-idrefs-type-attributes-using-sqlprefix-sqlxml-40"></a>使用 sql:prefix 建立 Valid ID、IDREF 和 IDREFS 類型屬性 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  屬性可以指定為識別碼類型屬性。 然後可以使用指定為 IDREF 或 IDREFS 的屬性來參考 ID 類型屬性，啟用文件之間的連結。  
  
 ID、IDREF 和 IDREFS 會對應至 PK/FK (主索引鍵/外部索引鍵) 在資料庫中的關聯性，但是有一些差異。 在 XML 文件中，ID 類型屬性的值必須是相異的。 如果**CustomerID**並**OrderID**屬性會指定為 XML 文件中 ID 型別必須是相異的這些值。 然而在資料庫中，CustomerID 和 OrderID 資料行的值可以相同  (例如，CustomerID = 1 且 OrderID = 1 在資料庫中是有效的)。  
  
 若要讓識別碼、IDREF 和 IDREFS 屬性是有效的：  
  
-   識別碼的值在 XML 文件中必須是唯一的。  
  
-   針對每一個 IDREF 和 IDREFS，參考的識別碼值都必須在 XML 文件中。  
  
-   ID、IDREF 和 IDREFS 的值必須是具名 Token  (例如，整數值 101 不能是 ID 值)。  
  
-   ID、 IDREF 和 IDREFS 類型的屬性無法對應至類型的資料行**文字**， **ntext**，或**映像**或任何其他二進位資料類型 (例如**時間戳記**)。  
  
 如果 XML 文件包含多個識別碼，請**sql: prefix**以確定值是唯一的註解。  
  
 請注意， **sql: prefix**註釋不能搭配 XSD 固定屬性。  
  
## <a name="examples"></a>範例  
 若要使用下列範例建立工作範例，您必須符合某些需求。 如需詳細資訊，請參閱 <<c0> [ 如需執行 SQLXML 範例的需求](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)。  
  
### <a name="a-specifying-id-and-idrefs-types"></a>A. 指定 ID 和 IDREFS 類型  
 在下列結構描述中， **\<客戶 >** 元素所組成**\<順序 >** 子項目。 **\<順序 >** 項目也具有子元素 **\<OrderDetail >** 項目。  
  
 **OrderIDList**屬性**\<客戶 >** 為 IDREFS 類型屬性，是指**OrderID**屬性 **\<順序 >** 項目。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
                 parent="Sales.Customer"  
                 parent-key="CustomerID"  
                 child="Sales.SalesOrderHeader"  
                 child-key="CustomerID" />  
    <sql:relationship name="OrderOrderDetail"  
                 parent="Sales.SalesOrderHeader"  
                 parent-key="SalesOrderID"  
                 child="Sales.SalesOrderDetail"  
                 child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
               sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                   sql:relationship="OrderOrderDetail"   
                   maxOccurs="unbounded" >  
                  <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="ProductID" type="xsd:string" />  
                   <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
               </xsd:element>  
             </xsd:sequence>  
             <xsd:attribute name="SalesOrderID"   
                            type="xsd:ID" sql:prefix="ord-" />  
             <xsd:attribute name="OrderDate" type="xsd:date" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CustomerID" type="xsd:string" />  
    <xsd:attribute name="OrderIDList" type="xsd:IDREFS"   
                   sql:relation="Sales.SalesOrderHeader" sql:field="SalesOrderID"  
                   sql:relationship="CustOrders" sql:prefix="ord-">  
    </xsd:attribute>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>針對結構描述測試範例 XPath 查詢  
  
1.  複製上述的結構描述程式碼，並將其貼到文字檔中。 將檔案儲存為 sqlPrefix.xml。  
  
2.  複製下列範本，並將其貼到文字檔中。 將檔案儲存在與 sqlPrefix.xml 相同的目錄中，並儲存為 sqlPrefixT.xml。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="sqlPrefix.xml">  
        /Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     針對對應結構描述 (sqlPrefix.xml) 指定的目錄路徑，相對於儲存範本的目錄。 您也可以指定絕對路徑，例如：  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlPrefix.xml"  
    ```  
  
3.  建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。  
  
     如需詳細資訊，請參閱 [使用ADO執行SQLXML查詢](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
 以下是部份結果：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" OrderIDList="ord-43860 ord-44501 ord-45283 ord-46042">  
    <Order SalesOrderID="ord-43860" OrderDate="2001-08-01" CustomerID="1">  
      <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
      ...  
    </Order>  
    ...  
 </Customer>  
</ROOT>  
```  
  
  
