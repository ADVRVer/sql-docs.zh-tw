---
title: 在位置路徑中設定選擇述詞（SQLXML）
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 84a3eade8a706e95b3ddba72d96e37d8fabf1fd3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "75256002"
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a>在位置路徑 (SQLXML 4.0) 中指定選取述詞
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  述詞會篩選與軸有關的節點集 (與 SELECT 陳述式中的 WHERE 子句相似)， 並指定在方括號之間。 對於節點集內要篩選的每一個節點，該節點會當做內容節點，而且節點集內的節點數目會當做內容大小，然後評估述詞運算式。 如果述詞運算式評估該節點為 TRUE，則產生的節點集會包含該節點。  
  
 XPath 也允許以位置為基礎的篩選。 評估為數字的述詞運算式會選取該序數節點。 例如，位置路徑 `Customer[3]` 會傳回第三客戶。 但是不支援這類數值述詞， 只支援傳回布林值的述詞運算式。  
  
> [!NOTE]  
>  如需 XPath 的 xpath 實作為限制的詳細資訊，以及它與 W3C 規格之間的差異，請參閱[使用 XPath 查詢的簡介 &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/introduction-to-using-xpath-queries-sqlxml-4-0.md)。  
  
## <a name="selection-predicate-example-1"></a>選取述詞：範例1  
 下列 XPath 運算式（位置路徑）會從目前的內容節點選取所有** \<客戶>** 專案子系，其值為 ALFKI 的**CustomerID**屬性：  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 在這個 XPath 查詢中，`child` 和 `attribute` 是軸的名稱。 `Customer``Customer`是節點測試（如果是** \<元素節點>**，則為 TRUE，因為** \<元素>** 是`child`軸的主要節點類型）。 `attribute::CustomerID="ALFKI"` 是述詞。 在述詞中`attribute` ，是軸而且`CustomerID`是節點測試（如果**CustomerID**是內容節點的屬性，則為 TRUE，因為** \<屬性>** 是**屬性**軸的主要節點類型）。  
  
 使用縮寫語法，XPath 查詢也可以指定為：  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a>選取述詞：範例2  
 下列 XPath 運算式（位置路徑）會從目前的內容節點中選取具有**SalesOrderID**屬性且值為1的所有** \<Order>** 孫系：  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 在這個 XPath 運算式中，`child` 和 `attribute` 是軸的名稱。 `Customer`、`Order` 和 `SalesOrderID` 是節點測試。 `attribute::OrderID="1"` 是述詞。  
  
 使用縮寫語法，XPath 查詢也可以指定為：  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a>選取述詞：範例3  
 下列 XPath 運算式（位置路徑）會從目前的內容節點選取所有** \<客戶>** 具有一或多個** \<連絡人>** 子系的子系：  
  
```  
child::Customer[child::ContactName]  
```  
  
 這個範例假設** \<連絡人>** 是 XML 檔中** \<Customer>** 元素的子項目，在批註式 XSD 架構中稱為*元素中心對應*。  
  
 在這個 XPath 運算式中，`child` 是軸的名稱。 `Customer`是節點`Customer`測試（如果是>節點的** \<元素**，則為 TRUE，因為** \<元素>** 是`child`軸的主要節點類型）。 `child::ContactName` 是述詞。 在述詞中`child` ，是軸而且`ContactName`是節點測試（如果`ContactName`是>節點的** \<元素**，則為 TRUE）。  
  
 此運算式只會傳回具有** \<[連絡人]>** 專案子系之內容節點的** \<客戶>** 專案子系。  
  
 使用縮寫語法，XPath 查詢也可以指定為：  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a>選取述詞：範例4  
 下列 XPath 運算式會選取** \<** 內容節點的客戶>專案子系，而不會有** \<連絡人>** 元素子系：  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 這個範例假設** \<連絡人>** 是 XML 檔中** \<Customer>** 元素的子項目，而且資料庫中不需要 [連絡人] 欄位。  
  
 在此範例中，`child` 為軸。 `Customer`是節點測試（如果`Customer`是> 節點的\<元素，則為 TRUE）。 `not(child::ContactName)` 是述詞。 在述詞中`child` ，是軸而且`ContactName`是節點測試（如果`ContactName`是> 節點的\<元素，則為 TRUE）。  
  
 使用縮寫語法，XPath 查詢也可以指定為：  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a>選取述詞：範例5  
 下列 XPath 運算式會從目前的內容節點中選取所有** \<客戶>** 具有**CustomerID**屬性的子系：  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 在此範例中`child` ，是軸而且`Customer`是節點測試（如果`Customer`是> 節點\<的元素，則為 TRUE）。 `attribute::CustomerID` 是述詞。 在述詞中`attribute` ，是軸， `CustomerID`而是述詞（如果`CustomerID`是>節點的** \<屬性**，則為 TRUE）。  
  
 使用縮寫語法，XPath 查詢也可以指定為：  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a>選取述詞：範例 6  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 支援在述詞中包含交叉乘積的 XPath 查詢，如下列範例所示：  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 這個查詢會選取所有客戶，其方式是使用任何 `Order`，其中 `OrderDate` 要等於任何 `ShipDate` 的 `Order`。  
  
## <a name="see-also"></a>另請參閱  
 [批註式 XSD 架構簡介 &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)   
 [用戶端 XML 格式 &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
