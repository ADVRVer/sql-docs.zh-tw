---
title: data 函數 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:data function
- data function [XQuery]
ms.assetid: 511b5d7d-c679-4cb2-a3dd-170cc126f49d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6ac37c6d3a55be4f11a4ad925a950724d5d791d7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934834"
---
# <a name="data-accessor-functions---data-xquery"></a>資料存取子函式 - data (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  傳回指定的每個項目的具類型的值 *$arg*。  
  
## <a name="syntax"></a>語法  
  
```  
  
fn:data ($arg as item()*) as xdt:untypedAtomic*  
```  
  
## <a name="arguments"></a>引數  
 *$arg*  
 其具類型值將會傳回的項目序列。  
  
## <a name="remarks"></a>備註  
 下列規定適用於具類型的值：  
  
-   不可部份完成值的具類型值，就是不可部份完成值。  
  
-   文字節點的具類型值是文字節點的字串值。  
  
-   註解的具類型值是註解的字串值。  
  
-   處理指示的具類型值是處理指示的內容，不含處理指示目標名稱。  
  
-   文件節點的具類型值是它的字串值。  
  
 下列規定適用於屬性和元素節點：  
  
-   如果屬性節點是具有 XML 結構描述類型的類型，它的具類型值也隨之為具類型值。  
  
-   如果屬性節點是不具型別，其具類型的值相當於傳回的執行個體的字串值**xdt: untypedatomic**。  
  
-   如果尚未輸入項目節點，其具類型的值相當於傳回的執行個體的字串值**xdt: untypedatomic**。  
  
 下列規定適用於具類型的元素節點：  
  
-   如果項目具有簡單內容型別**data （)** 傳回項目的具類型的值。  
  
-   如果節點是複雜類型，包括 xs: anytype， **data （)** 傳回靜態錯誤。  
  
 雖然使用**data （)** 函式通常是選擇性的如下列範例中，指定所示**data （)** 函式可明確增加查詢可讀性。 如需詳細資訊，請參閱 < [XQuery 基本概念](../xquery/xquery-basics.md)。  
  
 您無法指定**data （)** 上建構 XML，如下列所示：  
  
```  
declare @x xml  
set @x = ''  
select @x.query('data(<SomeNode>value</SomeNode>)')  
```  
  
## <a name="examples"></a>範例  
 本主題提供 XQuery 範例，針對 XML 執行個體儲存在各種**xml**類型資料行中的 AdventureWorks 資料庫。  
  
### <a name="a-using-the-data-xquery-function-to-extract-typed-value-of-a-node"></a>A. 使用 data() XQuery 函數擷取節點的具類型值  
 下列查詢說明如何**data （)** 函數用來擷取屬性、 項目，以及文字節點的值：  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query(N'  
 for $pd in //p1:ProductDescription  
 return   
    <Root   
      ProductID = "{ data( ($pd//@ProductModelID)[1] ) }"   
      Feature =   "{ data( ($pd/p1:Features/wm:Warranty/wm:Description)[1] ) }" >  
    </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 以下是結果：  
  
```  
<Root ProductID="19" Feature="parts and labor"/>  
```  
  
 如所述， **data （)** 函式是選擇性的當您建構屬性時。 如果您未指定**data （)** 函式，它會隱含假設。 下列查詢產生與上一個查詢相同的結果：  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
      for $pd in //p1:ProductDescription  
         return   
          <Root    
                ProductID = "{ ($pd/@ProductModelID)[1] }"    
                Feature =   "{ ($pd/p1:Features/wm:Warranty/wm:Description)[1] }" >  
           </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 下列範例說明中的執行個體**data （)** 函式是必要。  
  
 在下列查詢中， **$pd / pd/p1:specifications/material / 材料**會傳回 <`Material`> 項目。 此外，**資料 ($pd/pd/p1:specifications/material/Material)** 傳回的字元資料類型為 xdt: untypedatomic，因為 <`Material`> 是不具型別。 當輸入是不具型別、 結果**data （)** 型別為**xdt: untypedatomic**。  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
      for $pd in //p1:ProductDescription  
         return   
          <Root>  
             { $pd/p1:Specifications/Material }  
             { data($pd/p1:Specifications/Material) }  
           </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 以下是結果：  
  
```  
<Root>  
  <Material>Almuminum Alloy</Material>Almuminum Alloy  
</Root>  
```  
  
 在下列查詢中， **data($pd/p1:Features/wm:Warranty)** 會傳回靜態錯誤，因為 <`Warranty`> 是複雜類型的項目。  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
 <Root>  
   {     /p1:ProductDescription/p1:Features/wm:Warranty }  
   { data(/p1:ProductDescription/p1:Features/wm:Warranty) }  
 </Root>  
 ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID = 23  
```  
  
## <a name="see-also"></a>另請參閱  
 [針對 xml 資料類型的 XQuery 函式](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
