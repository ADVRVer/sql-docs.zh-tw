---
description: Exists (MDX)
title: 存在 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9c879d9091c692cfa7a93490b34c70ad84fa81c4
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193970"
---
# <a name="exists-mdx"></a>Exists (MDX)


  傳回屬於第一個指定集合並且與第二個指定集合中一或多個 Tuple 同時存在的 Tuple 集合。 這個函數會手動執行自動存在功能自動執行的動作。 如需自動存在的詳細資訊，請參閱 [MDX &#40;Analysis Services&#41;的重要概念 ](/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services)。  
  
 如果提供了選擇性的 \<Measure Group Name> ，函數會傳回與第二個集合中的一或多個元組存在的元組，以及在指定之量值群組的事實資料表中具有相關聯資料列的元組。  
  
## <a name="syntax"></a>語法  
  
```  
  
Exists( Set_Expression1 , Set_Expression2 [, MeasureGroupName] )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression1*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Set_Expression2*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *MeasureGroupName*  
 指定量值群組名稱的有效字串運算式。  
  
## <a name="remarks"></a>備註  
  
1.  指定 MeasureGroupName 引數時，量值群組資料列的量值包含 null 值有助於 **存在** 。 這是這種形式的存在與非空白函數之間的差異：如果這些量值的 NullProcessing 屬性設定為 [保留]，這表示當針對 cube 的該部分執行查詢時，量值會顯示 Null 值;非空白一律會從具有 Null 量值的集合移除元組，而 MeasureGroupName 引數則不會篩選具有相關聯之量值群組資料列的元組，即使量值為 Null 也是如此。  
  
2.  如果使用 *MeasureGroupName* 參數，結果將取決於參考的量值群組中是否有可見的量值;如果參考的量值群組中沒有可見的量值，則不論 *Set_Expression1* 和 *Set_Expression2*的值為何，EXISTS 都一律會傳回空集合。  
  
## <a name="examples"></a>範例  
 住在加州的客戶：  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
) ON 1   
FROM [Adventure Works]  
  
```  
  
 住在加州並且有銷售額的客戶：  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 有銷售額的客戶：  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, , "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 購買自行車的客戶：  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Product].[Product Categories].[Category].&[1]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [Mdx 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX&#41;的交叉結合 &#40;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [非空白的 &#40;MDX&#41;](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40;MDX&#41;](../mdx/isempty-mdx.md)  
  
