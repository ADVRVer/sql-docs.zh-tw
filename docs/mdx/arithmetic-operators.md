---
description: 算術運算子
title: 算術運算子 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 995e7ce1cb6a3c5d06db1042c00f945ec01e1be6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494991"
---
# <a name="arithmetic-operators"></a>算術運算子


  您可以使用多維度運算式 (MDX) 中的算術運算子，執行任何算術計算，包括加、減、乘與除。  
  
 MDX 支援下表中列出的算術運算子。  
  
|運算子|描述|  
|--------------|-----------------|  
|[+ (加)](../mdx/add-mdx.md)|兩個數字相加。|  
|[/ (除)](../mdx/divide-mdx-operator-reference.md)|以一個數目除以另一個數目。|  
|[* (乘)](../mdx/multiply-mdx.md)|兩個數目相乘。|  
|[- (減)](../mdx/subtract-mdx.md)|兩個數字相減。|  
|^ (乘冪)|計算某一個數字的次方數。|  
  
> [!NOTE]  
>  MDX 不包含用來取得某個數字之平方根的函數。 若要取得某個數字的平方根，請使用 ^ 運算子將它乘至 0.5 的乘冪。  
  
## <a name="order-of-precedence"></a>優先順序  
 下列規則決定算術運算子在 MDX 運算式中的優先順序：  
  
-   運算式中的算術運算子如果不止一個，MDX 就會先計算乘法與除法，然後再計算減法與加法。  
  
-   運算式中所有的算術運算子具有相同層級的優先順序時，執行順序為由左至右。  
  
-   先計算括號中的運算式，再計算其他所有運算。  
  
## <a name="see-also"></a>另請參閱  
 [Mdx 運算子參考 &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [運算子 &#40;MDX 語法&#41;](../mdx/operators-mdx-syntax.md)  
  
  
