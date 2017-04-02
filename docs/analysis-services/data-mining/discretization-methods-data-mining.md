---
title: "分隔方法 (資料採礦) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "內容類型 [資料採礦]"
  - "分隔 [Analysis Services]"
  - "資料行 [資料採礦]，離散化"
  - "THRESHOLDS 方法"
  - "CLUSTERS 方法"
  - "DiscretizationBuckets 屬性"
  - "AUTOMATIC 方法"
  - "EQUAL_AREAS 方法"
  - "編寫 [資料採礦]"
ms.assetid: 02c0df7b-6ca5-4bd0-ba97-a5826c9da120
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 29
---
# 分隔方法 (資料採礦)
  有些用於在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中建立資料採礦模型的演算法需要特定內容類型，才能正確運作。 例如， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法無法使用連續資料行做為輸入，也無法預測連續值。 另外，有些資料行可能包含太多值，使得演算法不容易識別資料中的模式來建立模型。  
  
 在這些情況下，您可以分隔資料行中的資料，以便使用演算法來產生採礦模型。 *「離散化」* (Discretization) 是將值放入值區內的程序，以產生有限數目的可能狀態。 值區本身會被視為已排序且會分隔值。 您可以分隔數值和字串資料行。  
  
 您有許多方法可用於分隔資料。 如果資料採礦方案使用關聯式資料，則您可以設定 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 屬性的值來控制用於分組資料的值區數。 預設的值區數為 5。  
  
 如果資料採礦方案使用於自線上分析處理 (Online Analytical Processing, OLAP) Cube 的資料，則資料採礦演算法會使用下列方程式來自動計算要產生的值區數，其中 n 是資料行中相異資料值的數目：  
  
 `Number of Buckets = sqrt(n)`  
  
 如果您不想要 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 計算值區數目，則可使用 <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> 屬性來手動指定值區數目。  
  
 下表描述您可用於分隔 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中之資料的方法。  
  
|分隔方法|說明|  
|---------------------------|-----------------|  
|**AUTOMATIC**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會決定要使用的分隔方法。|  
|**CLUSTERS**|演算法會將資料分成群組，流程是先取樣定型資料、初始化為一些隨機點，然後使用 Expectation Maximization (EM) 群集方法來執行 Microsoft 群集演算法的數次反覆運算。 **CLUSTERS** 方法很有用，因為它在任何分佈曲線上都可以運作。 不過，它比其他分隔方法需要更多的處理時間。<br /><br /> 這個方法只能用於數值資料行。|  
|**EQUAL_AREAS**|演算法會將資料分成數個值的數目相同之群組。 這個方法最適合標準分佈曲線，但如果分佈中有大量的值集中在連續資料的群組中，則效果不佳。 例如，如果有一半項目的成本是 0，則有一半的資料將會出現在曲線的單一點之下。 在這樣的分佈中，這個方法會將資料再細分，以建立成多個區域的相等分隔。 這樣會產生不精確的資料呈現。|  
  
## 備註  
  
-   您可以使用 **EQUAL_AREAS** 方法來分隔字串。  
  
-   **CLUSTERS** 方法使用 1000 筆隨機取樣記錄來離散化資料。 如果您不想要演算法取樣資料，請使用 **EQUAL_AREAS** 方法。  
  
  
  
## 請參閱＜  
 [內容類型 &#40;資料採礦&#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [內容類型 &#40;DMX&#41;](../../dmx/content-types-dmx.md)   
 [資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [採礦結構 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [資料類型 &#40;資料採礦&#41;](../../analysis-services/data-mining/data-types-data-mining.md)   
 [採礦結構資料行](../../analysis-services/data-mining/mining-structure-columns.md)   
 [資料行散發 &#40;資料採礦&#41;](../../analysis-services/data-mining/column-distributions-data-mining.md)  
  
  