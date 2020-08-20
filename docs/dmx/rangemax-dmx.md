---
description: RangeMax (DMX)
title: RangeMax (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1f7c3b58dde656e3afa07e9c53f1dca1c8116369
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487706"
---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  傳回針對分隔式資料行探索之預測值區的高端。  
  
## <a name="syntax"></a>語法  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>套用至  
 純量資料行。  
  
## <a name="return-type"></a>傳回類型  
 純量值。  
  
## <a name="remarks"></a>備註  
 **RangeMax**函數可以在[SELECT DISTINCT FROM &#60;model &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)查詢中使用。 搭配這種查詢類型使用時，純量資料行參考可以包含可預測或輸入的連續或分隔資料行。  
  
 搭配 [SELECT FROM &#60;model&#62; 預測聯結 &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)時， **RangeMin**、 **RangeMid**和 **RangeMax** 函數會傳回指定之值區的實際界限值。 例如，您若是執行分隔式資料行的預測，查詢就會傳回分隔式資料行中的預測值區號碼。 **RangeMin**、 **RangeMid**和**RangeMax**函數描述預測指定的值區。 當 **RangeMax** 函式搭配預測聯結語句使用時，純量資料行參考只可包含離散、可預測的資料行。  
  
## <a name="examples"></a>範例  
 下列範例傳回 Decision Tree 採礦模型中 Yearly Income 連續資料行的最小值、最大值及平均值。  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組 &#40;DMX&#41; 函數參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41;函數 &#40;](../dmx/functions-dmx.md)   
 [&#40;DMX&#41;的一般預測函數 ](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
  
