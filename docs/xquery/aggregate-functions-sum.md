---
title: sum 函數（XQuery） |Microsoft Docs
description: 瞭解會傳回數位序列總和的 XQuery 函數 sum （）。
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
- sum function [XQuery]
- fn:sum function
ms.assetid: 12288f37-b54c-4237-b75e-eedc5fe8f96d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b6efd2cc3d5793d4524c4ab3d058a6375d23892
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84886926"
---
# <a name="aggregate-functions---sum"></a>彙總函式 - sum
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  傳回數字序列的總和。  
  
## <a name="syntax"></a>語法  
  
```  
  
fn:sum($arg as xdt:anyAtomicType*) as xdt:anyAtomicType  
```  
  
## <a name="arguments"></a>引數  
 *$arg*  
 將計算其總和之不可部份完成值的順序。  
  
## <a name="remarks"></a>備註  
 所有傳遞至**sum （）** 的不可部份完成數值型別，都必須是相同基底類型的子類型。 可接受的基底類型為三個內建的數值基底類型或 xdt:untypedAtomic。 xdt:untypedAtomic 類型的值會轉換為 xs:double。 如果有混合的這些類型，或如果傳遞其他類型的其他值，就會引發靜態錯誤。  
  
 **Sum （）** 的結果會收到傳入類型的基底類型，例如 Xdt： untypedAtomic 的案例中的 xs： double，即使輸入是選擇性的，也是空的序列。 如果輸入在靜態上是空的，則結果是 0，並具有靜態和動態的 xs:integer 類型。  
  
 **Sum （）** 函數會傳回數值的總和。 如果 xdt： untypedAtomic 值無法轉換為 xs： double，則會在輸入序列中忽略此值 *$arg*。 如果輸入是動態計算出的空序列，則會傳回所用基底類型的值 0。  
  
 發生溢位或超出範圍的例外狀況時，此函數會傳回執行階段錯誤。  
  
## <a name="examples"></a>範例  
 本主題針對 XML 實例提供 XQuery 範例，這些實例是儲存在資料庫的各種**XML**類型資料行中 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 。  
  
### <a name="a-using-the-sum-xquery-function-to-find-the-total-combined-number-of-labor-hours-for-all-work-center-locations-in-the-manufacturing-process"></a>A. 使用 sum() XQuery 函數，尋找製造過程中所有工作中心位置的總合併工時數  
 下列查詢會尋找有儲存製造指示的所有產品型號之製造過程中，所有工作中心位置的總工時數。  
  
```  
SELECT Instructions.query('         
   declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
  <ProductModel PMID= "{ sql:column("Production.ProductModel.ProductModelID") }"         
  ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >         
   <TotalLaborHrs>         
     { sum(//AWMI:Location/@LaborHours) }         
   </TotalLaborHrs>         
 </ProductModel>         
    ') as Result         
FROM Production.ProductModel         
WHERE Instructions is not NULL         
```  
  
 以下是部份結果。  
  
```  
<ProductModel PMID="7" ProductModelName="HL Touring Frame">  
   <TotalLaborHrs>12.75</TotalLaborHrs>  
</ProductModel>  
<ProductModel PMID="10" ProductModelName="LL Touring Frame">  
  <TotalLaborHrs>13</TotalLaborHrs>  
</ProductModel>  
...  
```  
  
 若不想傳回 XML 格式的結果，您可以撰寫查詢來產生關聯式結果，如下列查詢所示：  
  
```  
SELECT ProductModelID,         
        Name,         
        Instructions.value('declare namespace   
      AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
    sum(//AWMI:Location/@LaborHours)', 'float') as TotalLaborHours         
FROM Production.ProductModel         
WHERE Instructions is not NULL          
```  
  
 以下是部份結果：  
  
```  
ProductModelID Name                 TotalLaborHours         
-------------- -------------------------------------------------  
7              HL Touring Frame           12.75                   
10             LL Touring Frame           13                      
43             Touring Rear Wheel         3                       
...  
```  
  
### <a name="implementation-limitations"></a>實作限制  
 以下為其限制：  
  
-   只支援**sum （）** 的單一引數版本。  
  
-   如果輸入是動態計算出的空序列，則會傳回所用基底類型的值 0，而不是 xs:integer 類型。  
  
-   **Sum （）** 函數會將所有整數對應到 xs： decimal。  
  
-   不支援 xs： duration 類型值的**sum （）** 函數。  
  
-   不支援跨越基底類型界限的混合類型。  
  
-   Sum （（xs： double （"INF"），xs： double （"-INF"）））會引發網域錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [針對 xml 資料類型的 XQuery 函數](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
