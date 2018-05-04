---
title: MDX 運算子參考 (MDX) |Microsoft 文件
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
dev_langs:
- kbMDX
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], operators
- operators [MDX]
- MDX [Analysis Services], operators
ms.assetid: 1cdb8c31-a5f6-4430-b509-f81344f4622a
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: cd4aaa3024b113cdc0f724db0d4635ecb22c4172
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-operator-reference-mdx"></a>MDX 運算子參考 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多維度運算式 (MDX) 語言支援算術、邏輯、比較、集合、字串與一元運算子。 下表列出支援的運算子以及它們的描述。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|Description|  
|-----------|-----------------|  
|[-& #40;註解 & #41;& #40;MDX & #41;](../mdx/comment-mdx-operator-reference.md)|指出使用者提供的註解文字。|  
|[-&#40;除了&#41; &#40;MDX&#41;](../mdx/except-mdx-operator.md)|執行集合運算，傳回兩個集合間的差異、移除重複的成員。|  
|[-&#40;負數&#41; &#40;MDX&#41;](../mdx/negative-mdx.md)|執行一元運算，這項運算會傳回數值運算式的負值。|  
|[-&#40;減去&#41; &#40;MDX&#41;](../mdx/subtract-mdx.md)|執行算術運算，將一個數字從另一個數字減去。|  
|[&#42;&#40;Crossjoin&#41; &#40;MDX&#41;](../mdx/crossjoin-mdx-operator-reference.md)|執行集合運算，傳回兩個集合的交叉乘積。|  
|[&#42;&#40;乘&#41; &#40;MDX&#41;](../mdx/multiply-mdx.md)|執行兩個數目相乘的算術運算。|  
|[&#40;分割&#41; &#40;MDX&#41;](../mdx/divide-mdx-operator-reference.md)|執行算術運算，將一個數字除以另一個數字。|  
|[^&#40;電源&#41; &#40;MDX&#41;](../mdx/power-mdx.md)|執行算術運算，將一個數字乘至另一個數字的乘冪。|  
|[註解 & #40;MDX & #41;](../mdx/comment-mdx.md)|指出使用者提供的註解文字。|  
|[& #40;註解 & #41;& #40;MDX & #41;](../mdx/comment-mdx-double-slash.md)|指出使用者提供的文字。|  
|[:&#40;範圍&#41; &#40;MDX&#41;](../mdx/range-mdx.md)|執行傳回一個自然順序集合的集合運算，其中會以兩個指定成員做為結束點，並將介於這兩個指定成員之間的所有成員當做集合的成員。|  
|[+&#40;新增&#41; &#40;MDX&#41;](../mdx/add-mdx.md)|執行兩個數目相加的算術運算。|  
|[+&#40;正數&#41; &#40;MDX&#41;](../mdx/positive-mdx.md)|執行一元運算，這項運算會傳回數值運算式的正值。|  
|[+&#40;字串串連&#41; &#40;MDX&#41;](../mdx/string-concatenation-mdx.md)|執行字串作業，串連兩個以上的字元字串、Tuple 或字串與 Tuple 的組合。|  
|[+ &#40;Union&#41; &#40;MDX&#41;](../mdx/union-mdx-operator-reference.md)|執行集合運算，傳回兩個集合的聯集、移除重複項。|  
|[&#60;&#40;小於&#41; &#40;MDX&#41;](../mdx/less-than-mdx.md)|執行比對作業，判斷某個 MDX 運算式的值是否小於另一個 MDX 運算式的值。|  
|[&#60;=&#40;小於或等於&#41; &#40;MDX&#41;](../mdx/less-than-or-equal-to-mdx.md)|執行比對作業，判斷某個 MDX 運算式的值是否小於或等於另一個 MDX 運算式的值。|  
|[&#60;&#62;&#40;不等於&#41; &#40;MDX&#41;](../mdx/not-equal-to-mdx.md)|執行比對作業，判斷某個 MDX 運算式的值是否不等於另一個 MDX 運算式的值。|  
|[=&#40;等於&#41; &#40;MDX&#41;](../mdx/equal-to-mdx.md)|執行比對作業，判斷某個 MDX 運算式的值是否等於另一個 MDX 運算式的值。|  
|[&#62;&#40;大於&#41; &#40;MDX&#41;](../mdx/greater-than-mdx.md)|執行比對作業，判斷某個 MDX 運算式的值是否大於另一個 MDX 運算式的值。|  
|[&#62;=&#40;大於或等於&#41; &#40;MDX&#41;](../mdx/greater-than-or-equal-to-mdx.md)|執行比對作業，判斷某個 MDX 運算式的值是否大於或等於另一個 MDX 運算式的值。|  
|[和&AMP;#40;MDX&AMP;#41;](../mdx/and-mdx.md)|在兩個數值運算式上執行邏輯結合。|  
|[是&AMP;#40;MDX&AMP;#41;](../mdx/is-mdx.md)|在兩個物件運算式上執行邏輯比較。|  
|[不&AMP;#40;MDX&AMP;#41;](../mdx/not-mdx.md)|在數值運算式上執行邏輯否定。|  
|[或者&AMP;#40;MDX&AMP;#41;](../mdx/or-mdx.md)|在兩個數值運算式上執行邏輯分離。|  
|[XOR &AMP;#40;MDX&AMP;#41;](../mdx/xor-mdx.md)|在兩個數值運算式上執行邏輯排除。|  
  
## <a name="see-also"></a>另請參閱  
 [MDX 語言參考 & #40;MDX & #41;](../mdx/mdx-language-reference-mdx.md)  
  
  
