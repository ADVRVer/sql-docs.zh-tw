---
title: 在 XPath 查詢 (SQLXML 4.0) 中指定算術運算子 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- arithmetic operators
- XPath operators [SQLXML]
- XPath queries [SQLXML], arithmetic operators
- operators [SQLXML]
ms.assetid: fdfbc87d-759f-4abc-acf5-a21de01f78d3
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4fe4e247041306cfd00854ae021e2fb5ec64c0b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36131669"
---
# <a name="specifying-arithmetic-operators-in-xpath-queries-sqlxml-40"></a>在 XPath 查詢中指定算術運算子 (SQLXML 4.0)
  下列範例示範如何在 XPath 查詢中指定算術運算子。 此範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。 如需此範例結構描述資訊，請參閱[範例註解式 XSD 結構描述的 XPath 範例&#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。  
  
## <a name="examples"></a>範例  
  
### <a name="a-specify-the--arithmetic-operator"></a>A. 指定 * 算術運算子  
 此 XPath 查詢會傳回 **\<OrderDetail >** 滿足指定的述詞的項目：  
  
```  
/child::OrderDetail[@UnitPrice * @Quantity = 12.350]  
```  
  
 在查詢中，`child`是軸和`OrderDetail`是節點測試 (TRUE 如果**OrderDetail**是**\<項目節點 >**，因為 **\<項目 >** 節點是主要節點`child`軸)。 所有 **\<OrderDetail >** 元素節點套用述詞中的測試，並且會傳回只在符合條件的節點。  
  
> [!NOTE]  
>  XPath 中的數字為雙精確度浮點數，而且在範例中比較浮點數會造成四捨五入。  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>針對對應的結構描述測試 XPath 查詢  
  
1.  複製[範例結構描述程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)並將它貼到文字檔。 將檔案儲存為 SampleSchema1.xml。  
  
2.  建立下列範本 (ArithmeticOperatorA.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /OrderDetail[@UnitPrice * @OrderQty = 12.350]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。 您也可以指定絕對路徑，例如：  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。  
  
     如需詳細資訊，請參閱[ADO to Execute SQLXML 4.0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
```  
Here is the partial result set of the template execution:    
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-710" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
   ...  
</ROOT>  
```  
  
  