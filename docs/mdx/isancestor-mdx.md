---
title: IsAncestor (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5cc8352b0d087b54a623cce892a05dfed29258b5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68105266"
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)


  傳回指定的成員是否為另一個指定成員的上階。  
  
## <a name="syntax"></a>語法  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>引數  
 *Member_Expression1*  
 傳回成員的有效多維度運算式 (MDX) 運算式。  
  
 *Member_Expression2*  
 傳回成員的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 **IsAncestor**函式會傳回 **，則為 true**第一個指定的成員是指定的第二個成員的上階。 否則，函數會傳回**false**。  
  
## <a name="example"></a>範例  
 下列範例會傳回 **，則為 true**如果 [Date]。 [會計年度]。CurrentMember 是 January 2003 的上階：  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另請參閱  
 [上階&#40;MDX&#41;](../mdx/ancestor-mdx.md)   
 [MDX 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
