---
title: "TopCount (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: TOPCOUNT
dev_langs: kbMDX
helpviewer_keywords: TopCount function
ms.assetid: 15026a8f-35c5-4307-8856-348f5c44bfd5
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 9e858e9ff073b96d2aba7d2f50aa49311b828b17
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="topcount-mdx"></a>TopCount (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  以遞減的順序排序集合，並傳回數值最高的指定元素數。  
  
## <a name="syntax"></a>語法  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *計數*  
 有效的數值運算式，會指定要傳回的 Tuple 數目。  
  
 *Numeric_Expression*  
 有效的數值運算式，這通常是傳回數字之資料格座標的多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 如果指定數值運算式， **TopCount**函式，依遞減順序排序，指定集合評估後數值運算式所指定的值根據指定的集合所指定集合中的 tuple。 排序集合之後, **TopCount**函式會傳回指定的值最高的 tuple 數目。  
  
> [!IMPORTANT]  
>  像[BottomCount](../mdx/bottomcount-mdx.md)函式， **TopCount**函數必會破壞階層架構。  
  
 如果未指定數值運算式，函數會傳回成員的集合以自然的順序，不進行任何排序，其運作方式[Head (MDX)](../mdx/head-mdx.md)函式。  
  
## <a name="examples"></a>範例  
 下列範例會依 Internet Sales Amount 傳回前 10 天：  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `TOPCOUNT([Date].[Date].[Date].MEMBERS, 10, [Measures].[Internet Sales Amount])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 下列範例會為 Bike 類別目錄傳回集合中的前五個成員，這個集合包含 Geography 維度 Geography 階層 City 層級以及 Date 維度 Fiscal 階層所有會計年度的成員組合，並根據 Reseller Sales Amount 量值排序 (以此集合中最大銷售數的成員開頭)。  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopCount  
   ({[Geography].[Geography].[City].Members   
      *[Date].[Fiscal].[Fiscal Year].Members}  
   , 5  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>請參閱＜  
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
