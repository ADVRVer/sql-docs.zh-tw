---
title: 軸 (MDX) |Microsoft 文件
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- AXIS
dev_langs:
- kbMDX
helpviewer_keywords:
- Axis function
ms.assetid: a3a60a1e-e266-4fa1-ae13-bae73544de33
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2a2272055859c2011d253537784eb2326bde1e93
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="axis-mdx"></a>Axis (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  傳回指定座標軸上的 Tuple 集合。  
  
## <a name="syntax"></a>語法  
  
```  
  
Axis(Axis_Number)  
```  
  
## <a name="arguments"></a>引數  
 *Axis_Number*  
 指定座標軸數目的有效數值運算式。  
  
## <a name="remarks"></a>備註  
 **軸**函數使用座標軸的以零為起始的位置來傳回座標軸上的 tuple 集合。 例如，`Axis(0)` 傳回 COLUMNS 座標軸，`Axis(1)` 傳回 ROWS 座標軸等等。 **軸**函式不能在篩選座標軸。 使用這個函數可讓導出成員得知正在執行之查詢的內容。 例如，您可以建立一個導出成員，讓它只提供資料列軸上選取之成員的總和。 它也可讓某一軸的定義相依於另一軸的定義。 例如，根據資料行軸上第一個項目的值來排序資料列軸的內容。  
  
> [!NOTE]  
>  座標軸僅能參考先前的座標軸。 例如，`Axis(0)` 必須在評估 COLUMNS 座標軸之後出現，如在 ROW 或 PAGE 座標軸上。  
  
## <a name="examples"></a>範例  
 下列範例查詢會示範如何使用 Axis 函數：  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SETTOSTR(AXIS(1))`  
  
 `SELECT MEASURES.AXISDEMO ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 下列範例會示範如何在導出成員內使用 Axis 函數：  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SUM(AXIS(1), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.AXISDEMO} ON 0,`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>請參閱  
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
