---
title: "CovarianceN (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COVARIANCEN
dev_langs:
- kbMDX
helpviewer_keywords:
- Covariancen function
ms.assetid: 1cc621cd-ffa0-40aa-91f0-bc5cb57f692b
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2eeee4c108965c00e847a8c3acdd60334e39000f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="covariancen-mdx"></a>CovarianceN (MDX)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  使用非偏誤母體公式 (除以 x-y 配對數)，在集合評估後傳回 x-y 配對值的樣本共變數。  
  
## <a name="syntax"></a>語法  
  
```  
  
CovarianceN(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Numeric_Expression_y*  
 有效的數值運算式，這通常是傳回表示 Y 軸數值之資料格座標的多維度運算式 (MDX) 運算式。  
  
 *Numeric_Expression_x*  
 有效的數值運算式，這通常是傳回表示 X 軸數值之資料格座標的多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 **CovarianceN**函式評估指定的集合，針對第一個數值運算式，以取得 y 軸的值。 此函數接著會針對第二個數值運算式 (如果已指定) 來評估指定的集合，以取得 X 軸的值集合。 如果沒有指定第二個數值運算式，此函數會使用指定集合中的資料格目前內容，做為 X 軸的值。  
  
 **CovarianceN**函式會使用非偏誤的母體公式。 這是相對於[共變數](../mdx/covariance-mdx.md)函式，會使用偏誤的母體公式 （除以 x-y 配對數）。  
  
> [!NOTE]  
>  **CovarianceN**函式會忽略空白資料格包含文字或邏輯值。 不過，此函數包括值為零的資料格。  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

