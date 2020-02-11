---
title: ValidMeasure （MDX） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b3bce4baf3dc3499621f67defd40a4579e9cd460
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037947"
---
# <a name="validmeasure-mdx"></a>ValidMeasure (MDX)


  在傳回指定 Tuple 的結果時，藉由強迫不適用的維度至其 All 層級 (如果不可彙總則是預設成員)，而傳回 Cube 中的量值。  
  
## <a name="syntax"></a>語法  
  
```  
  
ValidMeasure(Tuple_Expression)   
```  
  
## <a name="arguments"></a>引數  
 *Tuple_Expression*  
 傳回 Tuple 的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 **ValidMeasure**函式會傳回元組的值，忽略與元組傳回值的量值群組沒有關聯性的屬性。 基於兩個原因，屬性可以與量值無關：  
  
-   屬性的維度與 Tuple 中量值的量值群組沒有關聯性。  
  
-   屬性的維度與量值的量值群組沒有關聯性，但是資料粒度屬性不是索引鍵屬性，而且資料粒度屬性與 Tuple 中之屬性沒有直接關聯性。  
  
 這個函式所指定的行為是預設的伺服器端行為，並且是由量值群組物件上的**IgnoreUnrelatedDimensions**屬性所控制。  
  
 對於指定之 Tuple 中每個具資料粒度的屬性 (也就是說，Tuple 中的成員不是 All 成員時)，這類屬性的目前座標會移動如下：  
  
-   指定屬性成員的相關屬性會移至與目前成員同時存在的成員。  
  
-   指定屬性成員的相關屬性會移至與 All 成員 (如果是不可彙總的階層則是預設成員)。  
  
-   不相關的屬性會移至 All 成員 (根據量值)。  
  
## <a name="example"></a>範例  
 下列查詢示範 ValidMeasure 函數如何用來覆寫 IgnoreUnrelatedDimensions 屬性的行為。 在 Adventure Works Cube 中，銷售目標量值群組將 IgnoreUnrelatedDimensions 設為 False，因為日期維度於日曆季資料粒度聯結至此量值群組，這表示銷售配額量值預設會在日曆季下方傳回 Null (儘管 MDX 指令碼中也有計算會將值向下配置到月份層級)。 在導出量值中使用 ValidMeasure 函數，可以讓銷售配額量值的行為就如同 IgnoreUnrelatedDimensions 設為 True，並且強制銷售配額顯示目前日曆季的值。  
  
```  
WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])  
SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,  
[Date].[Calendar].MEMBERS ON 1  
FROM [Adventure Works]  
```  
  
 同樣地，銷售目標量值群組與促銷維度完全沒有關聯性，因此它會在促銷維度上任何階層的 All 成員下方傳回 Null。 您也可以使用 ValidMeasure 來變更此行為。  
  
 `WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])`  
  
 `SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,`  
  
 `[Promotion].[Promotions].members ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另請參閱  
 [Mdx 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
