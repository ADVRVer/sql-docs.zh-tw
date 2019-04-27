---
title: 屬性辨識索引標籤 （採礦模型檢視器） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.discrimination.f1
ms.assetid: 68323f23-121e-44fc-be85-6f9915d6d3c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f10fdf70b27f2bcea53ce32a1d64dec65e34893
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62650752"
---
# <a name="attribute-discrimination-tab-mining-model-viewer"></a>屬性辨識索引標籤 (採礦模型檢視器)
  使用 [屬性辨識] 索引標籤，即可比較輸入屬性的狀態以及查看它們與結果屬性如何相關。 先列出造成兩個選取的可預測屬性狀態之間最大差異的屬性值。  
  
 **如需詳細資訊：**[Microsoft 貝氏機率分類演算法](data-mining/microsoft-naive-bayes-algorithm.md)，[瀏覽模型，使用 Microsoft 貝氏機率分類檢視器](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>選項。  
 **重新整理檢視器內容**  
 在檢視器中重新載入採礦模型。  
  
 **採礦模型**  
 在目前採礦結構中選擇採礦模型。 採礦模型會自動在正確的自訂檢視器中開啟。  
  
 **Viewer**  
 選擇用來瀏覽選取之採礦模型的檢視器。 可以為每個模型選擇自訂檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。 還可以使用外掛程式檢視器 (如果有)。  
  
 **Attribute**  
 選擇可預測屬性。  
  
 **值 1**  
 選擇一種可預測屬性狀態，和 **[值 2]** 裡包含的狀態進行比較。  
  
 **值 2**  
 選取一種可預測屬性狀態，和 **[值 1]** 裡包含的狀態進行比較。 您也可以選取**所有其他的狀態**為比較值**值 1**與其補數-也就是所有其他值 1 以外的值。  
  
 **辨識率\<值 1 > 和\<值 2 >**  
 圖形包含下列資料行，描述目標屬性與輸入屬性的特定狀態如何相關。  
  
|值|描述|  
|-----------|-----------------|  
|**屬性**|採礦模型中的輸入屬性。|  
|**值**|列在 [屬性] 中之屬性的狀態。|  
|**喜好\<值 1 >**|長條表示目前屬性和值是否喜好 [值 1] 中所選的目標結果。|  
|**喜好\<值 2 >**|長條表示目前屬性和值是否喜好 [值 2] 中所選的目標結果。|  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [採礦模型檢視器 &#40;資料採礦模型設計師&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [資料採礦模型檢視器](data-mining/data-mining-model-viewers.md)  
  
  
