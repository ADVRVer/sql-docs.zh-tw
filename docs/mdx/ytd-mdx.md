---
title: "Ytd (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: YTD
dev_langs: kbMDX
helpviewer_keywords: Ytd function
ms.assetid: b77fdba2-d4a9-4271-8c21-c1f12eba526d
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: db4c92715c7d7fc8db500e90d42e4edf36c22106
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="ytd-mdx"></a>Ytd (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  從指定的成員，第一個同層級開始，並以指定成員結束，如同受條件約束相同的層級傳回成員的同層級集合*年*Time 維度中的層級。  
  
## <a name="syntax"></a>語法  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>引數  
 *Member_Expression*  
 傳回成員的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 如果未指定成員運算式，預設值是類型層級之第一個階層的目前成員*年*類型的第一個維度*時間*量值群組中。  
  
 **Ytd**函式是的捷徑函數[PeriodsToDate](../mdx/periodstodate-mdx.md)函式層級基礎屬性階層的 Type 屬性設定為其中*年*。 也就是說，`Ytd(Member_Expression)` 相當於 `PeriodsToDate(Year_Level_Expression,Member_Expression)`。 請注意，當 Type 屬性設定為不使用這個功能*FiscalYears*。  
  
## <a name="example"></a>範例  
 下列範例會傳回的 sum`Measures.[Order Quantity]`成員前, 八個月 2003年日曆年度中所包含的彙總`Date`維度中，從**Adventure Works** cube。  
  
```  
WITH MEMBER [Date].[Calendar].[First8MonthsCY2003] AS  
    Aggregate(  
        YTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First8MonthsCY2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 **Ytd**經常在組合中沒有指定參數，表示[CurrentMember &#40;MDX &#41;](../mdx/currentmember-mdx.md)函式會顯示累計的年度迄今總計在報表中，下列查詢中所示：  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>請參閱  
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
