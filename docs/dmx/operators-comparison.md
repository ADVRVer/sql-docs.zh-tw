---
title: 比較運算子 (DMX) |Microsoft 文件
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8049f2bad6e78ff301b460b1375a0a73807ccd8d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "37989680"
---
# <a name="operators---comparison"></a>運算子-比較
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  您可以使用任何資料採礦延伸模組 (DMX) 運算式中的純量資料中的比較運算子[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]。 比較運算子會評估為布林資料類型；它們會根據測試條件的結果而傳回 TRUE 或 FALSE。  
  
 下表會識別 DMX 支援的比較運算子。  
  
|運算子|描述|  
|--------------|-----------------|  
|[&#60;&#40;小於&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值小於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[&#62;&#40;大於&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值大於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[=&#40;等於&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值等於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[&#60;&#62;&#40;不等於&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值不等於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[&#60;=&#40;小於或等於&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值小於或等於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
|[&#62;=&#40;大於或等於&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|針對評估為非 Null 值的引數，如果左邊的引數值大於或等於右邊的引數值，傳回 TRUE；否則傳回 FALSE。 如果任一個引數或兩個引數都評估為 Null 值，則運算子會傳回 Null 值。|  
  
 您也可以在 DMX 陳述式與函數中使用比較運算子尋找條件。  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組&#40;DMX&#41;參考](../dmx/data-mining-extensions-dmx-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;函式參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法慣例](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [運算式&#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [一般預測函數&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [運算子&#40;DMX&#41;](../dmx/operators-dmx.md)   
 [結構和使用方式的 DMX 預測查詢](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 陳述式](../dmx/understanding-the-dmx-select-statement.md)  
  
  
