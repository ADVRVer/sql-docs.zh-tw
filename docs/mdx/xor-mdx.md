---
title: XOR (MDX) |Microsoft 文件
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eb0a91faaec7e5c2b6a7b2289e65989ba19b33e3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581870"
---
# <a name="xor-mdx"></a>XOR (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  在兩個數值運算式上執行邏輯排除。  
  
## <a name="syntax"></a>語法  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>參數  
 *Expression1*  
 傳回數值的有效多維度運算式 (MDX) 運算式。  
  
 *Expression2*  
 傳回數值的有效 MDX 運算式。  
  
## <a name="return-value"></a>傳回值  
 布林值，傳回**true**如果只有一個引數評估為**true**，否則**false**。  
  
## <a name="remarks"></a>備註  
 **XOR**運算子會將這兩個參數視為布林值 (零 （0) 做為**false**，否則**true**) 運算子執行邏輯排除之前。 下表將說明如何**XOR**運算子執行邏輯排除。  
  
|*Expression1*|*Expression2*|傳回值|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>另請參閱  
 [MDX 運算子參考&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
