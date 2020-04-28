---
title: 使用集合運算式 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1588d955e728830da4417160591a5c2b6c231473
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68893499"
---
# <a name="using-set-expressions"></a>使用集合運算式


  零個或多個 Tuple 之排序清單所組成的集合。 未包含任何 Tuple 的集合稱為空集合。  
  
 由零個或多個明確指定的 Tuple 而構成之集合的完整運算式 (嵌在大括號中)：  
  
 {[{ *Tuple_expression* | *Member_expression* } [，{ *Tuple_expression* | *Member_expression* }] ...]}  
  
 集合運算式中指定的成員運算式可轉換成單一成員 Tuple 運算式。  
  
## <a name="example"></a>範例  
 下列範例示範查詢的資料行軸和資料列軸上使用的兩個集合運算式：  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 在資料行軸上，  
  
 集合 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 是由 Measures 維度中的兩個成員所組成。 在資料列軸上，  
  
 {（[Product]。[產品類別]。[Category]. & [4]，[Date]。[行事曆]。[Calendar Year]. & [2004]），  
  
 （[Product]。[產品類別]。[Category]. & [1]，[Date]。[行事曆]。[Calendar Year]. & [2003]），  
  
 （[Product]。[產品類別]。[Category]. & [3]、[Date]。[行事曆]。[Calendar Year]. & [2004]）}  
  
 是由三個 tuple 所組成，每一個 tuple 都包含 Product 維度之 Product Category 階層上之成員及 Date 維度之 Calendar 階層上之成員的兩個明確參考。  
  
 如需傳回集合的函式範例，請參閱[使用成員、元組和 set &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx)。  
  
## <a name="see-also"></a>另請參閱  
 [MDX&#41;&#40;的運算式](../mdx/expressions-mdx.md)  
  
  
