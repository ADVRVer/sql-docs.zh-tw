---
title: "擷取 (MDX) |Microsoft 文件"
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
- EXTRACT
dev_langs:
- kbMDX
helpviewer_keywords:
- Extract function
ms.assetid: c0d27d31-e36e-4b7f-bb86-1e4707351392
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0e18c7ac7dcf37ce41bc7917c9d7170a815c1f58
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="extract-mdx"></a>Extract (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  從擷取的階層元素傳回 Tuple 集合。  
  
## <a name="syntax"></a>語法  
  
```  
  
Extract(Set_Expression, Hierarchy_Expression1 [,Hierarchy_Expression2, ...n] )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Hierarchy_Expression1*  
 傳回階層的有效多維度運算式 (MDX) 運算式。  
  
 *Hierarchy_Expression2*  
 傳回階層的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 **擷取**函數會傳回擷取之階層元素的 tuple 所組成的集合。 對於指定集合中的每個 Tuple，指定的階層成員會擷取至結果集中的新 Tuple。 此函數永遠會移除重複的 Tuple。  
  
 **擷取**函式會執行相反動作[Crossjoin](../mdx/crossjoin-mdx.md)函式。  
  
## <a name="examples"></a>範例  
 下列查詢會示範如何使用**擷取**函式所傳回的 tuple 集合上**NonEmpty**函式：  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `//Returns the distinct combinations of Customer and Date for all purchases`  
  
 `//of Bike Racks or Bike Stands`  
  
 `EXTRACT(`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `*`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `*`  
  
 `{[Product].[Product Categories].[Subcategory].&[26],[Product].[Product Categories].[Subcategory].&[27]}`  
  
 `*`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `)`  
  
 `,  [Customer].[Customer], [Date].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

