---
title: '* （乘）(DMX) |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f73e3e55045dd4ea9d4c2476540d2f7223d16eb0
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38037346"
---
# <a name="-multiply-dmx"></a>* (乘) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  執行以一個數目乘上另一個數目的算術運算。  
  
## <a name="syntax"></a>語法  
  
```  
  
Numeric_Expression * Numeric_Expression  
```  
  
#### <a name="parameters"></a>參數  
 *Numeric_Expression*  
 有效的資料採礦延伸模組 (DMX) 運算式，會傳回數值。  
  
## <a name="return-value"></a>傳回值  
 具有較高優先順序之參數資料類型的值。  
  
## <a name="remarks"></a>備註  
 兩個運算式的資料類型必須相同，或者其中一個運算式必須可以用隱含方式轉換為另一個運算式的資料類型。 如果一個運算式評估為 Null 值，運算子就會傳回 Null 值。  
  
## <a name="see-also"></a>另請參閱  
 [算術運算子&#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [資料採礦延伸模組&#40;DMX&#41;運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [運算子&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
