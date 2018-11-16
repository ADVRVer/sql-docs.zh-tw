---
title: SELECT INTO (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8a453fb545fd0a51b7d356c0d855813cea69f272
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602598"
---
# <a name="select-into-dmx"></a>SELECT INTO (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  建立一個以現有採礦模型的採礦結構為基礎的採礦模型。 **SELECT INTO**陳述式會藉由複製結構描述和其他不是實際演算法特定的資訊來建立新的採礦模型。  
  
## <a name="syntax"></a>語法  
  
```  
  
SELECT INTO <new model>   
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH[,] [FILTER(<expression>)]]  
FROM <existing model>  
```  
  
## <a name="arguments"></a>引數  
 *新的模型*  
 所建立之新模型的唯一名稱。  
  
 *演算法*  
 資料採礦演算法的提供者定義名稱。  
  
 *參數清單*  
 選擇性。 提供者自訂之演算法參數的逗號分隔清單。  
  
 *expression*  
 在定型資料上，評估為有效篩選條件的運算式。 如需有關可用來當做篩選條件的運算式的詳細資訊，請參閱[採礦模型的篩選&#40;Analysis Services-Data Mining&#41;](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)。  
  
 *現有的模型*  
 要複製之現有模型的名稱。  
  
## <a name="remarks"></a>備註  
 如果現有的模型已定型，當此陳述式執行時，會自動處理新模型。 否則，新模型會保持為未處理。  
  
 **SELECT INTO**現有模型的結構會與新模型的演算法相容時，只有陳述式才能運作。 因此，此陳述式最適用於快速建立與測試以相同演算法為基礎的模式。 如果您要變更演算法類型，新的演算法必須支援現有模型中每個資料行的資料類型，否則在處理模型時，可能會發生錯誤。  
  
 **WITH DRILLTHROUGH**子句可讓新的採礦模型上鑽研。 唯有您建立模型時，才能啟用鑽研。  
  
## <a name="example-1-altering-the-parameters-of-the-model"></a>範例 1：變更模型的參數  
 下列範例會建立新的採礦模型，根據現有的採礦模型， `TM_Clustering`，在[Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)。 在新的模型中，CLUSTER_COUNT 參數經過修改，使新模型中最多會有 5 個群集。 相反地，現有的模型使用預設值 10。  
  
```  
SELECT * INTO [New_Clustering]  
USING [Microsoft_Clustering] (CLUSTER_COUNT = 5)   
FROM [TM Clustering]  
```  
  
## <a name="example-2-adding-a-filter-to-the-model"></a>範例 2：將篩選器加入到模型中  
 下列範例根據現有的採礦模型建立新的採礦模型，並在模型上加入篩選器。 篩選器會將定型資料限制為僅住在特定區域的客戶。  
  
```  
SELECT * INTO [Clustering Europe Region]  
USING [Microsoft_Clustering] WITH FILTER(Region='Europe')  
FROM [TM Clustering]  
```  
  
> [!NOTE]  
>  套用到案例資料表的篩選器可以使用 SELECT INTO 陳述式進行變更，如此範例所示，不過，如果原始模型在巢狀資料表上包含篩選器，則無法使用此語法變更或移除巢狀資料表篩選器，但是會從原始模型，以原樣複製。 若要利用巢狀資料表上的不同篩選器建立模型，請使用 ALTER STRTUCTURE...ADD MODEL 語法。  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組&#40;DMX&#41;資料定義陳述式](../dmx/dmx-statements-data-definition.md)   
 [資料採礦延伸模組&#40;DMX&#41;資料操作陳述式](../dmx/dmx-statements-data-manipulation.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
