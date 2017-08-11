---
title: "將圖表加入至報表 （報表產生器及 SSRS） |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6b595dc-f775-4a53-8554-74a0bf9335ec
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a2d2ad7ae37e0f787709fb79afbf80ef3e584b5e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="add-a-chart-to-a-report-report-builder-and-ssrs"></a>將圖表加入至報表 (報表產生器及 SSRS)
  當您想要以 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 分頁報表的視覺格式摘要資料時，請使用圖表資料區域。 針對您要呈現的資料類型選擇適當的圖表類型相當重要。 因為這會影響以圖表形式放入資料時可以解譯資料的程度。 如需詳細資訊，請參閱 [圖表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)。  
  
 將圖表資料區加入至報表最簡單的方式就是執行新增圖表精靈。 該精靈提供直條圖、折線圖、圓形圖、橫條圖和區域圖。 您也可以透過手動方式，加入上述圖表以及其他的圖表類型。  
  
 將圖表資料區加入至設計介面之後，您可以將數值和非數值資料的報表資料集欄位拖曳到圖表的 [圖表資料] 窗格。 按一下圖表即可顯示 [圖表資料] 窗格，其中包含三個區域：[數列群組]、[類別群組] 和 [值]。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-chart-to-a-report-by-using-the-chart-wizard"></a>若要使用圖表精靈在報表中加入圖表  
  
1.  > [!NOTE]  
    >  您只能在報表產生器中使用圖表精靈。  
  
     在**插入**索引標籤上，按一下 **圖表**，然後按一下 **圖表精靈**。  
  
2.  請依照**新增**圖表精靈。  
  
3.  在 **[主資料夾]** 索引標籤上，按一下 **[執行]** 查看轉譯的報表。  
  
4.  在 **[執行]** 索引標籤上，按一下 **[設計]** 繼續處理報表。  
  
## <a name="to-add-a-chart-to-a-report"></a>若要將圖表加入至報表  
  
1.  建立報表，並定義資料集。 如需詳細資訊，請參閱[報表資料集 &#40;SSRS &#41;](../../reporting-services/report-data/report-datasets-ssrs.md).  
  
2.  在**插入**索引標籤上，按一下 **圖表**，然後按一下 **插入圖表**。  
  
3.  在設計介面上您要放置圖表左上角的位置按一下，然後拖曳到您要放置圖表右下角的位置。  
  
     **選取圖表類型** 對話方塊隨即出現。  
  
4.  選取您想要加入的圖表類型。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  按一下圖表，即可顯示**圖表資料**窗格。  
  
6.  將一或多個欄位加入**值**區域。 這些資訊將會繪製在值軸上。  
  
7.  加入群組欄位，以**類別目錄群組**區域。 當您將加入至這個欄位**類別目錄群組**區域中，為您自動建立群組欄位。 每一個群組都代表數列中一個資料點。  
  
8.  若要依類別目錄摘要資料，以滑鼠右鍵按一下資料欄位，然後按一下**數列屬性**。 在**類別**方塊中，從下拉式清單中選取 [分類] 欄位。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. 在 **[主資料夾]** 索引標籤上，按一下 **[執行]** 查看轉譯的報表。  
  
10. 在 **[執行]** 索引標籤上，按一下 **[設計]** 繼續處理報表。  
  
 在包含軸的圖表上 (如橫條圖和直條圖)，類別目錄軸可能不會顯示所有的類別目錄標籤。 如需如何變更軸標籤的詳細資訊，請參閱[指定軸間隔 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>另請參閱  
 [圖表 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [圖表類型 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [空白和 Null 資料點中圖表 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [教學課程： 將橫條圖加入至報表 （報表產生器）](http://go.microsoft.com/fwlink/?LinkId=198052)   
 [教學課程： 將橫條圖加入至報表 （報表設計工具）](http://go.microsoft.com/fwlink/?LinkId=198042)   
 [教學課程： 將圓形圖加入至報表 （報表產生器）](http://go.microsoft.com/fwlink/?LinkId=198051)   
 [教學課程： 將圓形圖加入至報表 （報表設計工具）](http://go.microsoft.com/fwlink/?LinkId=198041)  
  
  
