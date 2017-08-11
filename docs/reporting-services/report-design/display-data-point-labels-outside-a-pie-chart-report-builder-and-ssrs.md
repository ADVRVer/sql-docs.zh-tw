---
title: "顯示資料點標籤 （報表產生器及 SSRS） 在圓形圖外部 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 959b7574-cf43-470b-b592-4944d8a9948f
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2faa5b4e48f86c331ee45913844dc50c54c89e63
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs"></a>在圓形圖外部顯示資料點標籤 (報表產生器及 SSRS)
  在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中，圓形圖標籤經過最佳化，只會顯示在幾個資料扇形區上。 如果圓形圖包含的扇形區過多，標籤可能會重疊。 其中一種解決方法是將標籤顯示在圓形圖外部，這樣可能可以為較長的資料標籤創造更多空間。 如果您發現標籤仍會重疊，則可以透過啟用 3D 來建立更多的標籤空間。 如此可以縮減圓形圖的直徑，而在圖表外部建立更多空間。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-data-point-labels-inside-a-pie-chart"></a>在圓形圖內部顯示資料點標籤  
  
1.  將圓形圖加入到報表中。 如需詳細資訊，請參閱[將圖表加入至報表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)。  
  
2.  在設計介面上以滑鼠右鍵按一下圖表，然後選取 [顯示資料標籤]。  
  
### <a name="to-display-data-point-labels-outside-a-pie-chart"></a>在圓形圖外部顯示資料點標籤  
  
1.  建立圓形圖和顯示資料標籤。  
  
2.  開啟 [屬性] 窗格。  
  
3.  在設計介面上，按一下圓形圖本身，可在 [屬性] 窗格中顯示 [類別目錄] 屬性。  
  
4.  展開 **CustomAttributes** 節點。 圓形圖的屬性清單隨即顯示。  
  
5.  將 **PieLabelStyle** 屬性設定為 **Outside**。  
  
6.  將 **PieLineColor** 屬性設定為 **Black**。 PieLineColor 屬性定義每個資料點標籤的註標線。  
  
### <a name="to-prevent-overlapping-labels-displayed-outside-a-pie-chart"></a>若要防止在圓形圖外部顯示重疊的標籤  
  
1.  建立具有外部標籤的圓形圖。  
  
2.  在設計介面上以滑鼠右鍵按一下圓形圖外部 (但位於圖表框線內)，然後選取 [圖表區域屬性]。[圖表區域屬性] 對話方塊隨即出現。  
  
3.  在 [3D 選項] 索引標籤上，選取 [啟用 3D]。  
  
4.  如果希望圖表的標籤有更多的空間，但仍然以二維方式呈現，請將 [旋轉] 和 [傾斜] 屬性設定為 **0**。  
  
## <a name="see-also"></a>另請參閱  
 [圓形圖 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [將小扇區收集圓形圖 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)   
 [圓形圖 &#40; 上顯示百分比值報表產生器及 SSRS &#41;](../../reporting-services/report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
