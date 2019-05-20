---
title: 將 3D 效果新增至圖表 (報表產生器及 SSRS) | Microsoft Docs
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: ab9625d8-6557-4a4d-8123-eefa7c066ff5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: eb5fd8c6130f7f10effc9f9682fbde6063dca093
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65581672"
---
# <a name="chart-effects---add-3d-effects-report-builder"></a>圖表效果 - 新增 3D 效果 (報表產生器)
  三維 (3D) 效果可用來針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 分頁報表中的圖表提供深度及增加視覺效果。 例如，若要強調分裂式圓形圖的特殊扇區，則可以旋轉及變更圖表的檢視方塊，讓使用者能首先注意該扇區。 將 3D 效果套用至圖表時，所有的漸層色彩和影線樣式都會停用。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-apply-3d-effects-to-a-range-area-line-scatter-or-polar-chart"></a>將 3D 效果套用到範圍圖、區域圖、折線圖、散佈圖或極座標圖  
  
1.  以滑鼠右鍵按一下圖表區域內的任何位置，然後選取 [3D 效果]。 [圖表區域屬性] 對話方塊隨即出現。  
  
2.  在 [3D 選項] 中，選取 [啟用 3D] 選項。  
  
3.  (選擇性) 在 [3D 選項] 中，可以設定多種與 3D 角度及場景選項相關的屬性。 如需這些屬性的詳細資訊，請參閱 [圖表中的 3D、浮凸和其他效果 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/chart-effects-3d-bevel-and-other-report-builder.md)。  
  
4.  按一下 [確定] 。  
  
## <a name="to-apply-3d-effects-to-a-funnel-chart"></a>將 3D 效果套用到漏斗圖  
  
1.  以滑鼠右鍵按一下圖表區域內的任何位置，然後選取 [3D 效果]。 [圖表區域屬性] 對話方塊隨即出現。  
  
2.  在 [3D 選項] 中，選取 [啟用 3D] 選項。 按一下 [確定] 。  
  
3.  (選擇性) 若要自訂漏斗圖的視覺外觀，可以移至 [屬性] 窗格，然後變更漏斗圖特定的屬性。  
  
    1.  開啟 [屬性] 窗格。  
  
    2.  在設計介面上按一下漏斗的任何位置。 漏斗圖數列的屬性會顯示在 [屬性] 窗格中。  
  
    3.  在 [一般]  區段中，展開 [CustomAttributes]  節點。  
  
    4.  針對 [Funnel3DDrawingStyle] 屬性，選取漏斗是要顯示為圓形或方形。  
  
    5.  為 [Funnel3DRotationAngle] 屬性設定介於 -10 和 10 之間的值。 這會決定在 3D 漏斗圖上顯示的傾斜度。  
  
## <a name="to-apply-3d-effects-to-a-pie-chart"></a>將 3D 效果套用到圓形圖  
  
1.  以滑鼠右鍵按一下圖表區域內的任何位置，然後選取 [3D 效果]。 [圖表區域屬性] 對話方塊隨即出現。  
  
2.  在 [3D 選項] 中，選取 [啟用 3D] 選項。 按一下 [確定] 。  
  
3.  (選擇性) 在 [旋轉] 中鍵入整數值，代表圓形圖的水平旋轉。  
  
4.  (選擇性) 在 [傾斜] 中鍵入整數值，代表圓形圖的垂直傾斜旋轉。  
  
5.  按一下 [確定] 。  
  
## <a name="to-apply-3d-effects-to-a-bar-or-column-chart"></a>將 3D 效果套用到橫條圖或直條圖  
  
1.  以滑鼠右鍵按一下圖表區域內的任何位置，然後選取 [3D 效果]。 [圖表區域屬性] 對話方塊隨即出現。  
  
2.  選取 [啟用 3D] 選項。 按一下 [確定] 。  
  
3.  (選擇性) 選取 [啟用數列群集] 選項。 如果圖表包含多個橫條圖或直條圖數列，則這個選項會將數列顯示為群集。 依預設，多個橫條或直條數列會並列顯示。  
  
4.  按一下 [確定] 。  
  
5.  (選擇性) 若要對橫條圖或直條圖加入圓柱效果，請依照下列步驟執行：  
  
    1.  開啟 [屬性] 窗格。  
  
    2.  在設計介面上按一下數列中的任何橫條。 數列的屬性會顯示在 [屬性] 窗格中。  
  
    3.  在 [一般]  區段中，展開 [CustomAttributes]  節點。  
  
    4.  為 [DrawingStyle] 屬性指定 [圓柱] 值。  
  
## <a name="see-also"></a>另請參閱  
 [圖表中的 3D、浮凸和其他效果 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/chart-effects-3d-bevel-and-other-report-builder.md)   
 [格式化圖表 &#40;報表產生器和 SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [圖表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
