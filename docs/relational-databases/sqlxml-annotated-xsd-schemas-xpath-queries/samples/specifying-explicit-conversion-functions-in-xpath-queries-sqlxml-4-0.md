---
title: 在 XPath 查詢中使用轉換函數（SQLXML）
description: 瞭解如何在 SQLXML 4.0 XPath 查詢中指定明確轉換函數位符串（）和數位（）。
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c831a87004b410eeb5545fc98ce21ccee601f49d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773001"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a>在 XPath 查詢中指定明確轉換函數 (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  下列範例將示範如何在 XPath 查詢中指定明確轉換函數。 這些範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。 如需此範例架構的詳細資訊，請參閱[XPath 範例的範例批註式 XSD 架構 &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。  
  
## <a name="examples"></a>範例  
  
### <a name="a-use-the-number-explicit-conversion-function"></a>A. 使用 number() 明確轉換函數  
 **Number （）** 函數會將引數轉換成數位。  
  
 假設**ContactID**的值為非數值，則下列查詢會將**ContactID**轉換成數位，並將它與值4進行比較。 然後，此查詢會傳回內容節點的所有元素子系，其 **\<Employee>** **ContactID**屬性的數值為4：  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 您可以指定**屬性**軸（@）的快捷方式，而且因為**子**軸是預設值，所以可以從查詢中省略：  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 在關聯式詞彙中，此查詢會傳回**ContactID**為4的員工。  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>針對對應的結構描述測試 XPath 查詢  
  
1.  複製[範例架構程式碼](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。 將檔案儲存為 SampleSchema1.xml。  
  
2.  建立下列範本 (ExplicitConversionA.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。 您也可以指定絕對路徑，例如：  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。  
  
     如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
 這個範本執行的結果集如下：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a>B. 使用 string() 明確轉換函數  
 **String （）** 函數會將引數轉換成字串。  
  
 下列查詢會將**ContactID**轉換成字串，並將它與字串值 "4" 進行比較。 此查詢會傳回 **\<Employee>** 內容節點的所有元素子系，並具有字串值為 "4" 的**ContactID** ：  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 您可以指定**屬性**軸（@）的快捷方式，而且因為**子**軸是預設值，所以可以從查詢中省略：  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 就功能而言，這個函數與上一個範例查詢會傳回相同的結果，不過其評估是針對字串值而非數值 (亦即，數字 4) 進行。  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>針對對應的結構描述測試 XPath 查詢  
  
1.  複製[範例架構程式碼](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。 將檔案儲存為 SampleSchema1.xml。  
  
2.  建立下列範本 (ExplicitConversionB.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。 您也可以指定絕對路徑，例如：  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。  
  
     如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
 以下為範本執行的結果集：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  
