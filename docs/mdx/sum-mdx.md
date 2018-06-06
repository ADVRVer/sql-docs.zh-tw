---
title: Sum (MDX) |Microsoft 文件
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SUM
dev_langs:
- kbMDX
helpviewer_keywords:
- Sum function [MDX]
ms.assetid: 6c3db1e3-2c02-49f2-a0bf-cab0fb78c622
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 21b9c43749abc81180edc009f908a8b4b4f2febd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sum-mdx"></a>Sum (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  針對指定的集合進行評估之後，傳回數值運算式的總合。  
  
## <a name="syntax"></a>語法  
  
```  
  
Sum( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 有效的多維度運算式 (MDX) 集合運算式。  
  
 *Numeric_Expression*  
 有效的數值運算式，這通常是傳回數字之資料格座標的多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 如果有指定數值運算式，會使用該數值運算式評估集合，取得總合。 如果沒有指定數值運算式，則會在集合成員的目前內容中評估指定的集合，取得總合。 如果將 SUM 函數套用至非數值運算式，會產生未定義的結果。  
  
> [!NOTE]  
>  Analysis Services 在計算數字集合中的總和時會忽略 Null。  
  
## <a name="examples"></a>範例  
 下列範例會傳回 2001 和 2002 日曆年度 Product.Category 屬性階層之所有成員的 Reseller Sales Amounts 總合。  
  
```  
WITH MEMBER Measures.x AS SUM  
   ( { [Date].[Calendar Year].&[2001]  
         , [Date].[Calendar Year].&[2002] }  
      , [Measures].[Reseller Sales Amount]  
    )  
SELECT Measures.x ON 0  
,[Product].[Category].Members ON 1  
FROM [Adventure Works]  
```  
  
 下列範例會傳回 2002 年 7 月初至 7 月 20 日網際網路銷售的運費成本總合。  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 下列範例使用 WITH MEMBER 關鍵字和**總和**函式包含地理位置維度中 Country 屬性階層之 Canada 和 United States 成員的 Reseller Sales Amount 量值的總和的量值維度中定義的導出的成員。  
  
```  
WITH MEMBER Measures.NorthAmerica AS SUM   
      (  
         {[Geography].[Country].&[Canada]  
            , [Geography].[Country].&[United States]}  
       ,[Measures].[Reseller Sales Amount]  
      )  
SELECT {[Measures].[NorthAmerica]} ON 0,  
[Product].[Category].members ON 1  
FROM [Adventure Works]  
```  
  
 通常，**總和**函數搭配**CURRENTMEMBER**函式或函式，例如**YTD** ，來傳回因階層 currentmember 而異的。 例如，下列查詢會傳回從日曆年度開始到 Rows 軸上所顯示日期之間所有日期的 Internet Sales Amount 量值總和。  
  
 `WITH MEMBER MEASURES.YTDSUM AS`  
  
 `SUM(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDSUM} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 & #40;MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
