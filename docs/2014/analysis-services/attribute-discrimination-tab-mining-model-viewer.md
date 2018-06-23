---
title: 屬性辨識索引標籤 （採礦模型檢視器） |Microsoft 文件
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
- sql12.dm.miningmodeleditor.naivebayse.discrimination.f1
ms.assetid: 68323f23-121e-44fc-be85-6f9915d6d3c7
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 43ce0c215ac82eff64b688d6004dfd9c7af66266
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36034278"
---
# <a name="attribute-discrimination-tab-mining-model-viewer"></a>屬性辨識索引標籤 (採礦模型檢視器)
  使用 [屬性辨識] 索引標籤，即可比較輸入屬性的狀態以及查看它們與結果屬性如何相關。 先列出造成兩個選取的可預測屬性狀態之間最大差異的屬性值。  
  
 **如需詳細資訊，請參閱** [Microsoft 貝氏機率分類演算法](data-mining/microsoft-naive-bayes-algorithm.md)、[使用 Microsoft 貝氏機率分類檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。  
  
## <a name="options"></a>選項。  
 **重新整理檢視器內容**  
 在檢視器中重新載入採礦模型。  
  
 **採礦模型**  
 在目前採礦結構中選擇採礦模型。 採礦模型會自動在正確的自訂檢視器中開啟。  
  
 **檢視器**  
 選擇用來瀏覽選取之採礦模型的檢視器。 可以為每個模型選擇自訂檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。 還可以使用外掛程式檢視器 (如果有)。  
  
 **Attribute**  
 選擇可預測屬性。  
  
 **值 1**  
 選擇一種可預測屬性狀態，和 **[值 2]** 裡包含的狀態進行比較。  
  
 **值 2**  
 選取一種可預測屬性狀態，和 **[值 1]** 裡包含的狀態進行比較。 還可以選取 [所有其他的狀態]，以比較 [值 1] 中的值與其補數 (即值 1 以外的所有其他值)。  
  
 **辨識分數\<值 1 > 和\<值 2 >**  
 圖形包含下列資料行，描述目標屬性與輸入屬性的特定狀態如何相關。  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|**屬性**|採礦模型中的輸入屬性。|  
|**值**|列在 [屬性] 中之屬性的狀態。|  
|**喜好\<1 值 >**|長條表示目前屬性和值是否喜好 [值 1] 中所選的目標結果。|  
|**喜好\<值 2 >**|長條表示目前屬性和值是否喜好 [值 2] 中所選的目標結果。|  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦演算法&#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [採礦模型檢視器&#40;資料採礦模型設計工具&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [資料採礦模型檢視器](data-mining/data-mining-model-viewers.md)  
  
  