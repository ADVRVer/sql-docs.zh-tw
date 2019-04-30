---
title: LinRegR2 (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 42c703e703e8c557b4de8466a0cd1b686217fd4b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63136210"
---
# <a name="linregr2-mdx"></a>LinRegR2 (MDX)


  計算集合的線性迴歸，並傳回決定係數 R<sup>2</sup>。  
  
## <a name="syntax"></a>語法  
  
```  
  
LinRegR2(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Numeric_Expression_y*  
 有效的數值運算式，這通常是傳回表示 Y 軸數值之資料格座標的多維度運算式 (MDX) 運算式。  
  
 *Numeric_Expression_x*  
 有效的數值運算式，這通常是傳回表示 X 軸數值之資料格座標的多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 線性迴歸利用最小平方法，計算迴歸線方程式 (也就是說，數點之間的最佳直線)。 迴歸線有方程式如下，其中稱為斜率，而 b 是截距：  
  
 y = ax+b  
  
 **LinRegR2**函式會評估指定的 setagainst 第一個數值 expressionto 取得 y 軸的值。 此函數接著會針對第二個數值運算式 (如果已指定) 來評估指定的集合，以取得 X 軸的值。 如果第二個數值 expressionis 未指定，則此函數會使用其值為指定集合中的資料格目前內容的 x 軸。 不指定 x axisargument 經常搭配 「 時間 」 維度。  
  
 取得數點之後, **LinRegR2**函式會傳回統計 R<sup>2</sup> ，以描述線性方程式與點的符合程度。  
  
> [!NOTE]  
>  **LinRegR2**函式會忽略空資料格或包含文字或邏輯值的資料格。 不過，此函數包括值為零的資料格。  
  
## <a name="example"></a>範例  
 下列範例會傳回統計 R<sup>2</sup> ，以描述線性迴歸方程式，點銷售單位和商店銷售量值的符合程度。  
  
```  
LinRegR2(LastPeriods(10), [Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
