---
title: 不 (DMX) |Microsoft 文件
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 053eb905edb1379bfdc40ec010dc6d4efadcba26
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842841"
---
# <a name="not-dmx"></a>NOT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  在數值運算式上執行邏輯否定的邏輯運算子。  
  
## <a name="syntax"></a>語法  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>參數  
 *Expression1*  
 傳回數值的有效 DMX 運算式。  
  
## <a name="return-value"></a>傳回值  
 一個布林值，其中如果引數評估為 TRUE，就會傳回 FALSE；否則為 FALSE。  
  
## <a name="remarks"></a>備註  
 運算子執行邏輯否定之前，引數會當成布林值處理 (0 為 FALSE；否則為 TRUE）。 如果*Expression1*為 TRUE，則運算子會傳回 FALSE。 如果*Expression1*為 FALSE，則運算子會傳回 TRUE。 下表說明如何執行邏輯結合。  
  
|如果 Expression1 為|傳回值為|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組&#40;DMX&#41;運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [邏輯運算子&#40;DMX&#41;](../dmx/operators-logical.md)   
 [運算子&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
