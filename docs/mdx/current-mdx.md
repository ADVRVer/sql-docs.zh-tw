---
title: 目前 (MDX) |Microsoft 文件
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e30e2a7940223c7872151d96f05ff79ca919decf
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577690"
---
# <a name="current-mdx"></a>Current (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  反覆運算時從一個集合傳回目前的 Tuple。  
  
## <a name="syntax"></a>語法  
  
```  
  
Set_Expression.Current   
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 在反覆運算期間的每個步驟，進行運算的 Tuple 就是目前的 Tuple。 **目前**函式會傳回那個 tuple。 只有在集合上反覆運算時，這個函數才是有效的。  
  
 逐一查看集合的 MDX 函數包括[產生](../mdx/generate-mdx.md)函式。  
  
> [!NOTE]  
>  這個函數只能搭配已命名的集合 (使用集合別名或定義命名集) 使用。  
  
## <a name="examples"></a>範例  
 下列範例示範如何使用**目前**函式內**產生**:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of all Calendar Years crossjoined with`  
  
 `//all Product Categories`  
  
 `SET MyTuples AS CROSSJOIN(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `//Iterates through each tuple in the set and returns the name of the Calendar`  
  
 `//Year in each tuple`  
  
 `MEMBER MEASURES.CURRENTDEMO AS`  
  
 `GENERATE(MyTuples, MyTuples.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
