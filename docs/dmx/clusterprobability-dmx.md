---
title: ClusterProbability (DMX) |Microsoft 文件
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d4d8ce16bb07af07bd2bfd651cf5fc1ae15b7e08
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841681"
---
# <a name="clusterprobability-dmx"></a>ClusterProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  傳回輸入案例屬於指定之群集的機率。  
  
## <a name="syntax"></a>語法  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>適用於  
 唯有基礎資料採礦模型支援群集時，才能使用這個函數。  
  
## <a name="return-type"></a>傳回類型  
 純量值。  
  
## <a name="remarks"></a>備註  
 下列語法使用採礦模型內容結構描述資料列集，傳回採礦模型中存在的節點標題。  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 如需有關使用此語法的詳細資訊，請參閱[SELECT FROM&#60;模型&#62;。內容&#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)。 如需有關採礦模型內容結構描述資料列集的詳細資訊，請參閱[DMSCHEMA_MINING_MODEL_CONTENT 資料列集](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)。  
  
 如果\<節點標題 > 未指定，則函數會傳回輸入的案例屬於最可能的群集的機率。 使用**叢集**函數來傳回最可能的群集。  
  
## <a name="examples"></a>範例  
 下列範例傳回指定的案例存在標示為 Cluster 2 之叢集內的機率。  
  
```  
SELECT  
  ClusterProbability('Cluster 2')  
From  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>另請參閱  
 [叢集&#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [資料採礦延伸模組&#40;DMX&#41;函數參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [函式&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般預測函數&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
