---
title: 時序群集叢集設定檔 索引標籤 (採礦模型檢視器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.profiles.f1
ms.assetid: 44230895-0a42-4032-8d6c-0cdb8a2dbb8c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc1fd3f1b73d8b738f1ad8e38bc2be19e36b6fd1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068788"
---
# <a name="sequence-clustering-cluster-profiles-tab-mining-model-viewer"></a>時序叢集的叢集設定檔索引標籤 (採礦模型檢視器)
  [Microsoft 時序叢集檢視器] 中的 [叢集設定檔] 索引標籤提供每個叢集中所包含時序的色彩編碼檢視。  
  
 可以使用此時序叢集模型檢視，來快速查看模型所找到的時序的分組方式。 長時序的數目和短時序的數目一目了然。 還可以按一下叢集並顯示 **[採礦圖例]** ，來準確了解每個時序中各種色彩所表示的狀態。  
  
 **如需詳細資訊：**[Microsoft 時序叢集演算法](data-mining/microsoft-sequence-clustering-algorithm.md)，[瀏覽模型，使用 Microsoft 時序叢集檢視器  ](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>選項。  
 **重新整理檢視器內容**  
 在檢視器中重新載入採礦模型。  
  
 **採礦模型**  
 選擇包含在目前採礦結構中，您要檢視的採礦模型。 採礦模型會在其關聯的檢視器中開啟。  
  
 **檢視器**  
 選擇用來瀏覽選取之採礦模型的檢視器。 可以使用自訂檢視器，或 **[Microsoft 一般內容樹狀檢視器]**。 還可以使用外掛程式檢視器 (如果有)。  
  
 **顯示圖例**  
 選取此選項可顯示圖例，該圖例顯示叢集設定檔中顯示的色彩與狀態的文字值之間的相互關聯。  
  
 **長條圖列**  
 使用此選項可變更長條圖中包含的彩色列數。 如果總列數超出您選擇要顯示的列數，就會保留最重要的列，而其餘的列將會分組一起放入 **[其他]** 中。  
  
 **屬性** 和 **叢集設定檔**  
 圖表的此部分列出在模型中找到的時序叢集。  
  
 每個時序叢集是使用您在 **[長條圖列]** 選項中選取的狀態數目來顯示。  
  
 模型中每個叢集各顯示兩組長條圖，每組位於圖形中不同的資料列上：  
  
-   **\<屬性名稱 >.samples**： 此資料列中的長條圖顯示代表每個叢集之項目的時序。 在 DMX 詞彙中，它們是每個叢集的範例案例。  
  
-   **\<屬性名稱 >**： 此資料列中的長條圖描述叢集包含的所有項目及其整體分佈。 在 **[採礦圖例]** 可見時按一下長條圖，這會顯示每個項目的數值。  
  
 **狀態**  
 此資料行在圖表中是選擇性的，可透過選取 [顯示圖例] 選項來顯示或移除它。 **[狀態]** 資料行就對應的叢集長條圖中的哪種色彩表示哪種狀態提供了指南。  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦演算法&#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Microsoft 時序群集演算法](data-mining/microsoft-sequence-clustering-algorithm.md)   
 [採礦模型檢視器&#40;資料採礦模型設計工具&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [資料採礦模型檢視器](data-mining/data-mining-model-viewers.md)   
 [使用 Microsoft 時序叢集檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
  
