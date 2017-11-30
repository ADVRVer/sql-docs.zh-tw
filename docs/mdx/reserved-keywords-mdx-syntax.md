---
title: "保留的關鍵字 （MDX 語法） |Microsoft 文件"
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
dev_langs: kbMDX
helpviewer_keywords:
- reserved words [MDX]
- Multidimensional Expressions [Analysis Services], reserved words
- MDX [Analysis Services], reserved words
ms.assetid: 0baab5fb-bd04-4ab3-b99a-9f91f3470fbb
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 152ef57a3eeb881a1b3c21f5f15cf2e603bce864
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="reserved-keywords-mdx-syntax"></a>保留的關鍵字 (MDX 語法)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]保留為專用的特定關鍵字。 如需保留關鍵字的清單，請參閱[MDX 保留字](../mdx/mdx-reserved-words.md)。  
  
 保留關鍵字會遵循這些指導方針：  
  
-   除了由 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 定義的位置之外，您無法在多維度運算式 (MDX) 陳述式中的任何位置包括保留關鍵字 。  
  
-   資料庫的物件名稱不得與保留關鍵字完全相同。 如果有這種名稱，則必須使用分隔識別碼來參考物件。 雖然這個方法確實允許物件名稱作為保留關鍵字，但還是應該避免使用關鍵字來命名物件。  
  
-   使用會避免用到保留關鍵字的命名慣例。 如果物件名稱必須看起來像保留關鍵字，您可移除子音或母音。  
  
## <a name="see-also"></a>請參閱  
 [MDX 語法元素 &#40;MDX &#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
