---
title: 資料採礦延伸模組 (DMX) 函式參考 |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 68d57ac2db4149178a61424affef5e8948de0063
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070947"
---
# <a name="data-mining-extensions-dmx-function-reference"></a>資料採礦延伸模組 (DMX) 函數參考
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支援資料採礦延伸模組 (DMX) 語言中的數個函數。 函數會展開預測查詢的結果，以包含更深入描述預測的資訊。 函數也提供如何傳回預測結果的更多控制。 下表提供資源的連結，以協助您了解如何在 DMX 中使用函數。  
  
|函數|描述|  
|--------------|-----------------|  
|[一般預測函數&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)|列出可以搭配所有模型類型使用的函數，並提供關於如何查詢特定採礦模型類型之詳細資訊的連結。|  
|[DMX 預測查詢的結構和使用方式](../dmx/structure-and-usage-of-dmx-prediction-queries.md)|提供關於如何使用 DMX 建構預測查詢的概觀。|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|依據次序運算式，以遞增次序順序傳回資料表，其中包含指定數目的最底部資料列。|  
  
 下表列出 DMX 支援的函數。  
  
|函數|描述|  
|--------------|-----------------|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|依據次序運算式，以遞增次序順序傳回資料表，其中包含資料表運算式的最後 n 個項目資料列。|  
|[BottomPercent &#40;DMX&#41;](../dmx/bottompercent-dmx.md)|依據次序運算式，以遞增次序順序傳回資料表，其中包含符合指定百分比運算式之最小數目的最底部資料列。|  
|[BottomSum &#40;DMX&#41;](../dmx/bottomsum-dmx.md)|依據次序運算式，以遞增次序順序傳回資料表，其中包含符合指定總和運算式之最小數目的最底部資料列。|  
|[叢集 &#40;DMX&#41;](../dmx/cluster-dmx.md)|傳回最可能包含輸入案例的群集。|  
|[ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)|傳回輸入案例屬於群集的機率。|  
|[存在&#40;DMX&#41;](../dmx/exists-dmx.md)|如果指定之 SELECT 陳述式傳回的結果集至少包含一個資料列，就會傳回 True。|  
|[IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)|指出目前的節點是否從指定的節點衍生。|  
|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)|指出指定的節點是否包含案例。|  
|[IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)|指出某案例是否屬於測試案例集。|  
|[IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md)|指出某案例是否屬於定型案例集。|  
|[Lag &#40;DMX&#41;](../dmx/lag-dmx.md)|傳回目前案例之日期、與資料之最後日期之間的時間配量。|  
|[Predict &#40;DMX&#41;](../dmx/predict-dmx.md)|在指定的資料行上執行預測。|  
|[PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)|傳回指定之可預測資料行的已調整機率。|  
|[PredictAssociation &#40;DMX&#41;](../dmx/predictassociation-dmx.md)|在資料行中，預測關聯的成員資格。|  
|[PredictCaseLikelihood &#40;DMX&#41;](../dmx/predictcaselikelihood-dmx.md)|傳回輸入案例符合現有模型的可能性。 此函數只能搭配群集模型使用。|  
|[PredictHistogram &#40;DMX&#41;](../dmx/predicthistogram-dmx.md)|傳回代表指定資料行之長條圖的資料表。|  
|[PredictNodeId &#40;DMX&#41;](../dmx/predictnodeid-dmx.md)|傳回選取之案例的 NodeID。|  
|[PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)|傳回指定資料行的機率。|  
|[PredictSequence &#40;DMX&#41;](../dmx/predictsequence-dmx.md)|預測順序中的下一個值。|  
|[PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)|擷取指定之資料行的標準差值。|  
|[PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)|傳回資料行的支援值。|  
|[PredictTimeSeries &#40;DMX&#41;](../dmx/predicttimeseries-dmx.md)|傳回時間序列的未來值。|  
|[PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)|傳回指定資料行的變異數值。|  
|[RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)|傳回針對指定離散化資料行探索之預測值區的上限數值。|  
|[RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)|傳回針對指定離散化資料行探索之預測值區的中點數值。|  
|[RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)|傳回針對指定離散化資料行探索之預測值區的下限數值。|  
|[StructureColumn &#40;DMX&#41;](../dmx/structurecolumn-dmx.md)|傳回指定之資料表採礦結構資料行的值。|  
|[TopCount &#40;DMX&#41;](../dmx/topcount-dmx.md)|依據次序運算式，以遞減次序順序傳回資料表，其中包含指定數目的最頂部資料列。|  
|[TopPercent &#40;DMX&#41;](../dmx/toppercent-dmx.md)|依據次序運算式，以遞減次序順序傳回資料表，其中包含符合指定百分比運算式之最小數目的最頂部資料列。|  
|[TopSum &#40;DMX&#41;](../dmx/topsum-dmx.md)|依據次序運算式，以遞減次序順序傳回資料表，其中包含符合指定總和運算式之最小數目的最頂部資料列。|  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組&#40;DMX&#41;運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法慣例](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般預測函數&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [DMX 預測查詢的結構和使用方式](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 陳述式](../dmx/understanding-the-dmx-select-statement.md)  
  
  
