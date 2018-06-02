---
title: DrillupLevel (MDX) |Microsoft 文件
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19d6443857d53d835db4c395ddd43dc4a305ad8c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579450"
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  向下切入集合內在特定層級底下的成員。  
  
## <a name="syntax"></a>語法  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Level_Expression*  
 傳回層級的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 **DrillupLevel**函式會傳回一組成員以階層方式組織根據指定集合中包含的成員。 會保留指定集合中成員的順序。  
  
 如果指定層級運算式，則**DrillupLevel**函數來擷取指定的層級上面的那些成員建構集合。 如果指定層級運算式，而且在指定集合中沒有代表該指定層級的成員，則會傳回指定的集合。  
  
 如果沒有指定層級運算式，此函數只會擷取比指定集合中所參考之第一個維度的最低層級還要再高一個層級的那些成員，來建構集合。  
  
## <a name="example"></a>範例  
 下列範例會從第一個集合中傳回在 Subcategory 層級以上之成員的集合。  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
