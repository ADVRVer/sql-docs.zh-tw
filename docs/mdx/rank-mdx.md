---
title: 順位 (MDX) |Microsoft 文件
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ac8b41545063caa123eb678e5b2b0bda3b3a1e09
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580990"
---
# <a name="rank-mdx"></a>Rank (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  傳回指定集合中、指定 Tuple 的以一為基底次序。  
  
## <a name="syntax"></a>語法  
  
```  
  
Rank(Tuple_Expression, Set_Expression [ ,Numeric Expression ] )  
```  
  
## <a name="arguments"></a>引數  
 *Tuple_Expression*  
 傳回 Tuple 的有效多維度運算式 (MDX) 運算式。  
  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Numeric_Expression*  
 有效的數值運算式，這通常是傳回數字之資料格座標的多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 如果指定數值運算式，**陣序規範**函式會判斷指定之 tuple 的以一為陣序藉由評估指定的數值運算式對 tuple。 如果指定數值運算式，**陣序規範**函式會將相同的陣序指派給集合中的重複值的 tuple。 指派相同的順序給重複值，會影響集合中後續 Tuple 的順序。 例如，有個集合由以下 Tuple 構成：`{(a,b), (e,f), (c,d)}`。 Tuple `(a,b)` 和 Tuple `(c,d)` 擁有相同的值。 如果 Tuple `(a,b)` 的次序為 1，則 `(a,b)` 和 `(c,d)` 的次序都會是 1。 不過，Tuple `(e,f)` 的次序會是 3。 這個集合中可能不會有次序 2 的 Tuple。  
  
 如果未指定數值運算式，**陣序規範**函式會傳回 1 為基底的序數位置指定的 tuple。  
  
 **陣序規範**函式不會排序集合。  
  
## <a name="example"></a>範例  
 下列範例會傳回使用包含客戶和購買日期的 tuple 集合**篩選**， **NonEmpty**，**項目**，和**陣序規範**函式以尋找最後一個日期，每一位客戶購買。  
  
```  
WITH SET MYROWS AS FILTER  
   (NONEMPTY  
      ([Customer].[Customer Geography].MEMBERS  
         * [Date].[Date].[Date].MEMBERS  
         , [Measures].[Internet Sales Amount]  
      ) AS MYSET  
   , NOT(MYSET.CURRENT.ITEM(0)  
      IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))  
   )  
SELECT [Measures].[Internet Sales Amount] ON 0,  
MYROWS ON 1  
FROM [Adventure Works]  
```  
  
 下列範例會使用**順序**函式，而非**陣序規範**函式，來排名 City 階層的成員根據 Reseller Sales Amount 量值，然後依此次序顯示它們。 使用**順序**函數，先排序 City 階層的成員集合，排序是只進行一次並跟著線性掃描之前要呈現在排序順序。  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [順序&#40;MDX&#41;](../mdx/order-mdx.md)   
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
