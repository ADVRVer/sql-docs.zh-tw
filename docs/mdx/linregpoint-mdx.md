---
title: LinRegPoint (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cc47b5910f0d5323b1b7e29cd3313b36d615265c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63136066"
---
# <a name="linregpoint-mdx"></a>LinRegPoint (MDX)


  計算集合的線性迴歸，並傳回的值*y-intercept&lt*在迴歸線 y = ax + b x 的特定值。  
  
## <a name="syntax"></a>語法  
  
```  
  
LinRegPoint(Slice_Expression_x, Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引數  
 *Slice_Expression_x*  
 有效的數值運算式，這通常是傳回表示 slicer 座標軸數值之資料格座標的多維度運算式 (MDX) 運算式。  
  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Numeric_Expression_y*  
 有效的數值運算式，這通常是傳回表示 Y 軸數值之資料格座標的多維度運算式 (MDX) 運算式。  
  
 *Numeric_Expression_x*  
 有效的數值運算式，這通常是傳回表示 X 軸數值之資料格座標的多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 線性迴歸利用最小平方法，計算迴歸線方程式 (也就是說，數點之間的最佳直線)。 迴歸線有方程式如下，其中稱為斜率，而 b 是截距：  
  
 y = ax+b  
  
 **LinRegPoint**函式評估指定的集合，針對第二個數值運算式，以取得 y 軸的值。 此函數接著會針對第三個數值運算式 (如果已指定) 來評估指定的集合，以取得 X 軸的值。 如果沒有指定第三個數值運算式，此函數會使用指定集合中的資料格目前內容，做為 X 軸的值。 Time 維度經常不指定 X 軸引數。  
  
 一旦導出線性迴歸線，就會計算第一個數值運算式的方程式值，然後將它傳回。  
  
> [!NOTE]  
>  **LinRegPoint**函式會忽略空白資料格或包含文字的資料格。 不過，此函數包括值為零的資料格。  
  
## <a name="example"></a>範例  
 下列範例會根據 Unit Sales 和 Store Sales 之間的統計關聯性，傳回過去 10 個週期 Unit Sales 的預測值。  
  
```  
LinRegPoint([Measures].[Unit Sales],LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
