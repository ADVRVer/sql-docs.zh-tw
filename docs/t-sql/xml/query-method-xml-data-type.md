---
title: query() 方法 (xml 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8eb8570d260b1e30d3c0ecafa0f3bfd15065983
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "72278168"
---
# <a name="query-method-xml-data-type"></a>query() 方法 (xml 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

針對 **xml** 資料類型的執行個體指定 XQuery。 結果為 **xml** 類型。 該方法會傳回不具類型的 XML 執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>引數  
XQuery  
是字串類型的 XQuery 運算式，可查詢 XML 執行個體中的項目和屬性等 XML 節點。  
  
## <a name="examples"></a>範例  
此節提供一些使用 **xml** 資料類型的 query() 方法之範例。  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. 針對 xml 類型變數使用 query() 方法  
下列範例可宣告 **xml** 類型的 **\@myDoc** 變數並指派 XML 執行個體給它。 **query()** 方法可用以指定針對文件的 XQuery。  
  
查詢會擷取 <`ProductDescription`> 元素的 <`Features`> 子元素：  
  
```  
declare @myDoc xml  
set @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc.query('/Root/ProductDescription/Features')  
```  
  
下列輸出顯示結果：  
  
```  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>        
```  
  
### <a name="b-using-the-query-method-against-an-xml-type-column"></a>B. 使用針對 XML 類型資料行的 query() 方法  
在下列查詢中，**query()** 方法是用以指定 XQuery，以針對 **AdventureWorks** 資料庫中 **xml** 類型的 **CatalogDescription** 資料行進行查詢：  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
請注意，下列項目是從上一個查詢而來：  
  
-   CatalogDescription 資料行是具類型的 **xml** 資料行，這表示它有與其建立關聯的結構描述集合。 在 [XQuery 初構](../../xquery/modules-and-prologs-xquery-prolog.md)中，**namespace** 關鍵字可定義稍後要用於查詢主體的前置詞。  
  
-   **query()** 方法會建構 XML、具有 **ProductModelID** 屬性的 <`Product`> 元素，其中 **ProductModelID** 屬性值是從資料庫擷取而來。 如需 XML 建構的詳細資訊，請參閱 [XML 建構 &#40;XQuery&#41;](../../xquery/xml-construction-xquery.md)。  
  
-   WHERE 子句的 [exist() 方法 (XML 資料類型)](../../t-sql/xml/exist-method-xml-data-type.md) 只會尋找 XML 中包含 <`Warranty`> 項目的資料列。 同樣地，**namespace** 關鍵字可定義兩個命名空間的前置詞。  
  
下列輸出顯示部分結果：  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
請注意，query() 與 exist() 方法都會宣告 PD 前置詞。 在此情況下，您可以使用 WITH XMLNAMESPACES 先定義前置詞並在查詢中使用它。  
  
```  
WITH XMLNAMESPACES 
(  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM
)  
SELECT CatalogDescription.query('<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />')
       AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/PD:ProductDescription/PD:Features/WM:Warranty ') = 1;

```  
  
## <a name="see-also"></a>另請參閱  
 [使用 WITH XMLNAMESPACES 將命名空間加入至查詢](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [比較具類型的 XML 與不具類型的 XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [建立 XML 資料的執行個體](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml 資料類型方法](../../t-sql/xml/xml-data-type-methods.md)   
 [XML 資料修改語言 &#40;XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
