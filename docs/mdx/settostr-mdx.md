---
description: SetToStr (MDX)
title: SetToStr (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0317de06f3d68388fac5be752d26e27f0d373a89
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500441"
---
# <a name="settostr-mdx"></a>SetToStr (MDX)


  傳回對應至指定集合的多維度運算式 (MDX) 格式化字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 這個函數是用來將集合的字串表示傳送至外部函數，以進行剖析。 傳回的字串會以大括弧括住 {} ，並以逗號分隔集合中的每個專案。  
  
## <a name="example"></a>範例  
 下列範例會傳回包含 Geography.Country 屬性階層之所有成員的字串。  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
