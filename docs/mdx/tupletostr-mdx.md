---
title: TupleToStr (MDX) |Microsoft 文件
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7fb89e3529117ce83f37b83b15c3e32f9c085088
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581340"
---
# <a name="tupletostr-mdx"></a>TupleToStr (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  傳回多維度運算式 (MDX)–對應至指定 Tuple 的格式化字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
TupleToStr(Tuple_Expression)   
```  
  
## <a name="arguments"></a>引數  
 *Tuple_Expression*  
 傳回 Tuple 的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 這個函數是用來將 Tuple 的字串表示傳送至外部函數，以進行剖析。 所傳回的字串括在大括弧{}和每個成員，如果多個 tuple 中明確定義為以逗號分隔。  
  
## <a name="examples"></a>範例  
 下列範例會傳回字串 ([Date].[Calendar Year].&[2001],[Geography].[Geography].[Country].&[United States])：  
  
```  
WITH MEMBER Measures.x AS TupleToStr   
   (   
      ([Date].[Calendar Year].&[2001]  
         , [Geography].[Geography].[Country].&[United States]  
      )  
   )     
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 下列範例會傳回和上一個範例相同的字串。  
  
```  
WITH SET s AS   
   {  
      ([Date].[Calendar Year].&[2001],  
         [Geography].[Geography].[Country].&[United States]  
      )   
   }  
MEMBER Measures.x AS TupleToStr ( s.Item(0) )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
