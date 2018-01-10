---
title: "新增空白點至圖表 (報表產生器及 SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b056119-439f-494f-83cf-ee0c05dc6487
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 90c66d591f18bd541737ffaa03ea8f29d53d9710
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="add-empty-points-to-a-chart-report-builder-and-ssrs"></a>新增空白點至圖表 (報表產生器及 SSRS)
Null 值會顯示在圖表上，當做數列內資料點之間的空格或間距。 在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 分頁報表中，空點是指可以插入由 Null 值所建立之空格內的資料點。  
  
 根據預設，空點的計算方式是求得包含某個值之上一個和下一個資料點的平均值。 您可以變更這個值，好讓所有空白點都在零的地方插入。  
  
 如需詳細資訊，請參閱[圖表中的空白和 Null 資料點 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-empty-points-on-a-chart"></a>在圖表上指定空白點  
  
1.  開啟 [屬性] 窗格。  
  
2.  在設計介面上，以滑鼠右鍵按一下包含 Null 值的數列。 數列的屬性會顯示在 [屬性] 窗格中。  
  
3.  展開 **[EmptyPoint]** 節點。  
  
4.  為 Color 屬性選取色彩值。  
  
5.  在 **[EmptyPoint]** 節點中，展開 [標記] 節點。  
  
6.  為 MarkerType 屬性選取標記類型。  
  
    > [!NOTE]  
    >  您必須選取一個標記類型，以便將空點加入至橫條圖、直條圖或散佈圖。 但如果是區域圖、折線圖和雷達圖，則選取標記類型為選擇性的動作，因為該圖表會填入空白的空格或間距，而不需要指定標記。  
  
7.  設定空點的值。  
  
    1.  在 [屬性] 窗格中，展開 **[CustomAttributes]** 節點。  
  
    2.  設定 EmptyPointValue 屬性。 若要在上一個和下一個資料點的平均值處插入空點，請選取 **Average**。 若要在零處插入空點，請選取 **Zero**。  
  
## <a name="see-also"></a>另請參閱  
 [新增資料集篩選、資料區篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [圖表類型 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [新增刻度斷層至圖表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-scale-breaks-to-a-chart-report-builder-and-ssrs.md)   
 [圖表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
