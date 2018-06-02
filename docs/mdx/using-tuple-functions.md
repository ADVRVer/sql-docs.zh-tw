---
title: 使用 Tuple 函數 |Microsoft 文件
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a58be5cbd0ea4101f5be2ebb8e29c1669d7f09f4
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581630"
---
# <a name="using-tuple-functions"></a>使用 Tuple 函數
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Tuple 函數可以擷取集合的 Tuple，或是解析 Tuple 的字串表示法來擷取 Tuple。  
  
 Tuple 函數跟成員函數和集合函數一樣，對於交涉 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中找到的多維度結構而言不可或缺。  
  
 在 MDX 中，有三個 tuple 函數[目前&#40;MDX&#41;](../mdx/current-mdx.md)，[項目&#40;Tuple&#41; &#40;MDX&#41; ](../mdx/item-tuple-mdx.md)和[StrToTuple &#40;MDX&#41;](../mdx/strtotuple-mdx.md). 下列範例查詢會示範如何使用每一個函數：  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另請參閱  
 [函式&#40;MDX 語法&#41;](../mdx/functions-mdx-syntax.md)   
 [使用成員函式](../mdx/using-member-functions.md)   
 [使用集合函式](../mdx/using-set-functions.md)  
  
  
