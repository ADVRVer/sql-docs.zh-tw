---
description: 使用邏輯函數
title: 使用邏輯函數 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2a13f9fa95878277b164b37bb71e3d9af646d89f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340994"
---
# <a name="using-logical-functions"></a>使用邏輯函數


  邏輯函數可對物件及運算式執行邏輯作業或比較，然後傳回布林值。 多維度運算式 (MDX) 中必須要有邏輯函數，才能判斷成員的位置。  
  
 最常使用的邏輯函數是 **IsEmpty** 函數。 如需有關如何使用 **IsEmpty** 函數的詳細資訊，請參閱使用 [空值](../mdx/working-with-empty-values.md)。  
  
 下列查詢顯示如何使用 **IsLeaf** 和 **IsAncestor** 函數：  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另請參閱  
 [函數 &#40;MDX 語法&#41;](../mdx/functions-mdx-syntax.md)  
  
  
