---
title: "IsLeaf (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ISLEAF
dev_langs: kbMDX
helpviewer_keywords: IsLeaf function
ms.assetid: 54862bb3-acc2-4711-ac5a-faa9e9de3721
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: eaca03a46baf7db9215ba1bd1a6b7bd032dd6177
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="isleaf-mdx"></a>IsLeaf (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  傳回指定的成員是否為分葉成員。  
  
## <a name="syntax"></a>語法  
  
```  
  
IsLeaf(Member_Expression)   
```  
  
## <a name="arguments"></a>引數  
 *Member_Expression*  
 傳回成員的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 **IsLeaf**函式會傳回**true**如果指定的成員為分葉成員。 否則，函數會傳回**false**。  
  
## <a name="example"></a>範例  
 如果 [Date].[Fiscal].CurrentMember 是分葉成員，下列範例會傳回 TRUE：  
  
 `WITH MEMBER MEASURES.ISLEAFDEMO AS`  
  
 `IsLeaf([Date].[Fiscal].CURRENTMEMBER)`  
  
 `SELECT {MEASURES.ISLEAFDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>請參閱  
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
