---
title: "處理資料採礦物件 |Microsoft 文件"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing objects [Analysis Services]
- mining structures [Analysis Services]
- process [Analysis Services]
- mining structures [Analysis Services], creating
- mining structures [Analysis Services], how-to topics
- mining structures [Analysis Services], processing
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c05c204eab305b42ddce4a3114cd9162a921c7b2
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="processing-data-mining-objects"></a>處理資料採礦物件
  資料採礦物件在處理之前只是一個空容器。 *「處理」* (Processing) 資料採礦模型也稱為 *「定型」*(Training)。  
  
 **處理採礦結構** ：採礦結構會從外部資料來源取得資料 (依資料行繫結和使用方式中繼資料的定義)，並讀取資料。 系統會完整地讀取這項資料，再加以分析以擷取各種統計資料。 Analysis Services 會在本機快取中儲存資料的壓縮表示 (適合以資料採礦演算法進行分析)。 您可在模型經過處理後保存此快取或加以刪除。 依預設會儲存此快取。 如需詳細資訊，請參閱 [Process a Mining Structure](../../analysis-services/data-mining/process-a-mining-structure.md)(處理採礦結構)。  
  
 **處理採礦模型** ：採礦模型在處理之前是空的，只包含定義。 若要處理採礦模型，則該模型所依據的採礦結構必須已經過處理。 採礦模型在從採礦結構快取取得資料之後，會套用已在模型上建立的任何篩選，然後再透過演算法傳遞資料集來偵測模式。 採礦模型在經過處理之後，只會儲存處理的結果，而非資料本身。 如需詳細資訊，請參閱 [Process a Mining Model](../../analysis-services/data-mining/process-a-mining-model.md)(處理採礦模型)。  
  
 下列圖表說明在處理採礦結構和資料模型時的資料流程。  
  
 ![資料處理： 來源到結構到模型](../../analysis-services/data-mining/media/dmcon-modelarch.gif "資料處理： 來源到結構到模型")  
  
## <a name="viewing-the-results-of-processing"></a>檢視處理的結果  
 採礦結構經過處理之後會包含資料的壓縮表示，以供統計資料分析使用。 如果尚未清除快取，可以用下列方式存取此快取的資料：  
  
-   在模型上建立資料採礦延伸模組 (DMX) 查詢並鑽研至結構。 如需詳細資訊，請參閱 [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](../../dmx/select-from-model-cases-dmx.md)。  
  
-   請根據結構瀏覽模型，並使用使用者介面中的一個選項以鑽研至結構案例。 如需詳細資訊，請參閱 [Data Mining Model Viewers](../../analysis-services/data-mining/data-mining-model-viewers.md)(資料採礦模型檢視器) 或 [Drill Through to Case Data from a Mining Model](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)(鑽研採礦模型的案例資料)。  
  
-   在結構案例上建立 DMX 查詢。 如需詳細資訊，請參閱 [SELECT FROM &#60;structure&#62;.CASES](../../dmx/select-from-structure-cases.md)。  
  
 採礦模型經過處理之後只會包含衍生自分析的模式，以及模型結果與快取之定型資料的對應。 您可以瀏覽或查詢模型結果 (稱為 *「模型內容」*)，或者也可以查詢模型和結構案例 (若已存入快取)。  
  
 每個採礦模型的模型內容都是根據建立時所使用的演算法而定。 例如，如果某個模式是叢集模型，而另一個模型是決策樹模型，則即使模型使用的資料完全相同，模型的內容也會非常不同。 如需詳細資訊，請參閱[採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)。  
  
## <a name="processing-requirements"></a>處理需求  
 根據採礦模型只根據關聯式資料還是多維度資料來源，處理需求可能會有所差異。  
  
 如果是關聯式資料來源，處理作業只需要您建立定型資料，並在該資料上執行採礦演算法。 但是，根據 OLAP 物件的採礦模型 (例如維度和量值) 需要基礎資料處於已處理的狀態。 這可能需要處理多維度物件，才能擴展採礦模型。  
  
 如需詳細資訊，請參閱 [Processing Requirements and Considerations &#40;Data Mining&#41;](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md) (處理需求和考量 (資料採礦))。  
  
## <a name="see-also"></a>另請參閱  
 [鑽研查詢 &#40;資料採礦&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [採礦結構 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [採礦模型 & #40;Analysis Services-資料採礦 & #41;](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)   
 [邏輯架構 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/logical-architecture-analysis-services-data-mining.md)  
  
  

