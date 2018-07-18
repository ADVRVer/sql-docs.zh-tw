---
title: TopSum (MDX) |Microsoft 文件
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 853390f99f02352fd7814fcec208bba1508c03a7
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743407"
---
# <a name="topsum-mdx"></a>TopSum (MDX)


  為集合排序，並傳回頂端數個元素，這些元素的累積總數至少是指定的數值。  
  
## <a name="syntax"></a>語法  
  
```  
  
TopSum(Set_Expression, Value, Numeric_Expression)   
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *值*  
 有效的數值運算式，會指定用來與每個 Tuple 比較的值。  
  
 *Numeric_Expression*  
 有效的數值運算式，這通常是傳回量值的多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 **TopSum**函式會計算指定的集合，以遞減順序排序集合上評估指定的量值的總和。 然後，函數會傳回最高值的元素，這些元素之指定數值運算式的總計至少是指定值。 這個函數會傳回累計總計至少是指定值之集合的最小子集。 傳回從最大到最小排列的元素。  
  
> [!IMPORTANT]  
>  像[BottomSum](../mdx/bottomsum-mdx.md)函式， **TopSum**函數必會破壞階層架構。  
  
## <a name="example"></a>範例  
 下列範例會為 Bike 類別目錄傳回Geography 維度 Geography 階層中 City 層級之成員的最小集合，此集合的累計總計使用 Reseller Sales Amount 量值計算至少是總和 6,000,000 (以此集合中最大銷售數的成員開頭)。  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopSum  
   ({[Geography].[Geography].[City].Members}  
   , 6000000  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
