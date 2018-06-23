---
title: 屬性設定檔 索引標籤 （採礦模型檢視器） |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a6c9c5e0dfee13c8c0bd08ad5d1c6433d16ca7df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36035113"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a>屬性設定檔索引標籤 (採礦模型檢視器)
  可以使用 **[屬性設定檔]** 索引標籤，來查看貝氏機率分類模型狀態中輸入值的分佈如何影響結果屬性的每個狀態。 值的分佈會顯示為彩色長條圖，而且所有分佈都會以表格格式呈現，以便更輕鬆地比較值。  
  
 **如需詳細資訊，請參閱** [Microsoft 貝氏機率分類演算法](data-mining/microsoft-naive-bayes-algorithm.md)、[使用 Microsoft 貝氏機率分類檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>選項。  
 **重新整理檢視器內容**  
 在檢視器中重新載入採礦模型。  
  
 **採礦模型**  
 在目前採礦結構中選擇要檢視的採礦模型。 採礦模型會在其關聯的檢視器中開啟。  
  
 **檢視器**  
 選擇用來瀏覽選取之採礦模型的檢視器。 可以選擇為每個採礦模型提供的自訂檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。 還可以使用外掛程式檢視器 (如果有)。  
  
 **顯示圖例**  
 選取此選項可顯示圖例符號，該圖例符號會將 [狀態] 中的每個值對應至分佈圖表中使用的色彩。  
  
 **長條圖列**  
 選取長條圖中要包含多少個圖列。 如果圖列的總數超出您選擇要顯示的總數，就會保留最重要的圖列，並將其餘的圖列一起放入 **[其他]** 群組中。  
  
 **可預測**  
 從採礦模型選取可預測的資料行。  
  
 **屬性設定檔**  
 資料表包含下列資料行：  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|**屬性**|列出採礦模型中包含的採礦模型資料行。|  
|**狀態**|此為選擇性的資料行，用來描述屬性對應資料列之色彩所代表的狀態。 使用 **[顯示圖例]** 核取方塊即可加入或移除。|  
|**母體**|顯示整個結果集之屬性的散發。|  
|**針對可預測屬性狀態的資料行**|為可預測資料行的每個狀態顯示一個資料行，其中每個資料列都會對應至模型中的某個輸入屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦演算法&#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [採礦模型檢視器&#40;資料採礦模型設計工具&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [資料採礦模型檢視器](data-mining/data-mining-model-viewers.md)  
  
  