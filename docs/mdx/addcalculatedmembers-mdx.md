---
title: AddCalculatedMembers (MDX) |Microsoft 文件
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 18ccf4ad808c15945d82f1ca05616f0da878a7ca
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739387"
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (MDX)


  傳回藉由在指定集合中新增導出成員的方式所產生的集合。  
  
## <a name="syntax"></a>語法  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 根據預設，MDX 會在解析集合函數時排除導出成員。 **AddCalculatedMembers**函式會檢查在指定的集合運算式*如此，* 並包含為包含在範圍內之成員的同層級的導出的成員的集合運算式。  
  
> [!NOTE]  
>  此函數僅能搭配一維的集合運算式使用。  
  
## <a name="examples"></a>範例  
 以下範例示範此函數的用法。  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 下列範例會傳回`Measures.[Unit Price]`成員，以及中的所有導出成員**量值**維度中，從**Adventure Works** cube。  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
