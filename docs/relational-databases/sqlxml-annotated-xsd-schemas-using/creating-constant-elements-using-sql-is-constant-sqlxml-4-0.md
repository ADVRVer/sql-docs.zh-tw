---
title: '建立常數元素使用 sql: is-constant< (SQLXML 4.0) |Microsoft 文件'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 81ee34607d198e88eee397b9c9f254f2133d1b22
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32969383"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a>使用 sql:is-constant 建立常數元素 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  若要指定常數元素 — 也就是沒有對應到任何資料庫資料表或資料行的 XSD 結構描述的項目 — 您可以使用**sql: is-constant<** 註解。 此註解接受布林值 (0 = false，1 = true)。 可接受的值為 0、1、true 和 false。 **Sql: is-constant<** 可以沒有任何屬性的項目上指定註解。 如果該註解是在值為 True (或 1) 的元素上指定，該元素不會對應到資料庫，但是仍會出現在 XML 文件中。  
  
 **Sql: is-constant<** 附註可用於：  
  
-   將最上層元素加入到 XML 文件中。 XML 需要單一的最上層元素 (根元素) 供文件使用。  
  
-   建立容器元素，例如**\<訂單 >** 包裝所有訂單的項目。  
  
 **Sql: is-constant<** 可以加入標註 **\<complexType >** 項目。  
  
## <a name="examples"></a>範例  
 若要使用下列範例建立工作範例，您必須符合某些需求。 如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)。  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a>A. 指定 sql:is-constant 來加入容器元素  
 在這個註解式 XSD 結構描述，  **\<CustomerOrders >** 定義為常數元素指定**sql: is-constant<** 屬性值為 1。 因此，  **\<CustomerOrders >** 未對應到任何資料庫資料表或資料行。 此常數元素組成**\<順序 >** 子項目。  
  
 雖然 **\<CustomerOrders >** 不會對應到任何資料庫資料表或資料行中，事件仍會顯示為容器項目包含產生之 XML 中**\<順序 >** 子項目。  
  
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
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>針對結構描述測試範例 XPath 查詢  
  
1.  複製上述的結構描述程式碼，並將其貼到文字檔中。 將檔案儲存為 isConstant.xml。  
  
2.  複製下列範本，並將其貼到文字檔中。 將檔案儲存為 isConstantT.xml，並儲存在與儲存 isConstant.xml 相同的目錄中。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     為對應結構描述 (isConstant.xml) 指定的目錄路徑，是儲存範本之目錄的相對路徑。 您也可以指定絕對路徑，例如：  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。  
  
     如需詳細資訊，請參閱[ADO to Execute SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
 這是部分結果集：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
