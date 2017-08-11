---
title: "加入 Reporting Services 行動報表的導覽器 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e141f50e-49a9-46c6-983c-f656013aa07c
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 753cb1a6bc95c854d8a9457f6dc8a70867f2a6bd
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="add-navigators-to-reporting-services-mobile-reports"></a>Add navigators to Reporting Services mobile reports
在 [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]中，您加入 *「導覽器」* (Navigator)，以依時間或依選取項目來篩選視覺效果中的資料。 

導覽器與 Power BI 和 Excel 樞紐分析表中的交叉分析篩選器類似，但導覽器也有一些特有的特性。

**以時間為基礎的導覽器** 會選取落在特定時間範圍內的資料列，以篩選資料表。 

**以選取項目為基礎的導覽器** 會選取特定資料行值符合所選取索引鍵值，或是針對階層樹狀目錄時特定資料行值屬於所選取索引鍵值子樹狀目錄的資料列，以篩選資料表。 選擇導覽器有兩種類型：
* 選擇清單是可用來篩選行動報表的單一資料行資料表，與 Power BI 和 Excel 中的交叉分析篩選器類似。
* 計分卡方格也會篩選行動報表，也可以包含 
  
## <a name="time-navigators"></a>時間導覽器   
  
正如其名，您可以使用時間導覽器，來篩選依時間範圍所繫結的資料範圍。   
  
![SSMRP_TimeNav](../../reporting-services/mobile-reports/media/ssmrp-timenav.png)  
*在該時間範圍的預設設定四個折線圖左邊。在右側的折線圖是篩選器。*  
  
當您在預覽或 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] Web 入口網站中檢視報表時，請拖曳時間導覽器中的箭號來篩選報表的其餘部分。  
  
![SSMRP_TimeNavPreview](../../reporting-services/mobile-reports/media/ssmrp-timenavpreview.png)  
  
時間導覽器預設會篩選連接至時間型資料之報表中的所有視覺項目。 若資料表包含多個時間型資料行，則僅會使用第一個資料行執行篩選。 系列資料表可促進內嵌視覺效果以及決定行動報表的整體日期範圍。  
  
您可以從時間導覽器中斷視覺效果的連線。   
1. 選取視覺效果，然後選取 [**資料**] 索引標籤。  
2. 在**資料屬性**，選取**選項**。  
3. 清除**經過**核取方塊。  
  
   ![SSMRP_ClearTimeFilter](../../reporting-services/mobile-reports/media/ssmrp-cleartimefilter.png)  
  
## <a name="selection-lists"></a>選擇清單   
  
選擇清單會比對清單中所選取的值與所篩選資料表之每個資料列的指定資料行的值，以篩選行動報表中的資料。 

1. 從**配置**索引標籤，拖曳**選擇清單**設計介面，並調整其大小，您想要的方式。

2. 選取**資料** 索引標籤，然後在**資料屬性**窗格下的**金鑰**，選取資料表和資料行篩選。 

3. 在下**標籤**，選取將會顯示標籤的資料行。 索引鍵資料行與標籤資料行可相同。  
  
   若為階層樹狀目錄資料，選取父索引鍵資料行。  
  
4. 在設定資料屬性之後,**選擇清單篩選資料表**，選取要篩選的資料表和資料行來篩選。 此資料行需要比對選擇清單之索引鍵資料行中的值。 

針對行動報表中您要選擇清單篩選的每個視覺效果︰

1. 選取視覺效果中，選取**資料** 索引標籤，然後在**資料屬性**窗格中，選取**選項**欄位名稱旁邊。

   ![mobile-report-set-selection-list](../../reporting-services/mobile-reports/media/mobile-report-set-selection-list.png)

2. 下**經過**，選取 選取項目清單。

如果您在預覽或 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] Web 入口網站中檢視行動報表，並且在選擇清單中選取值，則會篩選行動報表中的其他視覺效果。

![mobile-report-selection-list-filtering](../../reporting-services/mobile-reports/media/mobile-report-selection-list-filtering.png) 
     
## <a name="scorecard-grid"></a>計分卡方格  
  
計分卡方格篩選的功能與選擇清單篩選非常類似，但也會顯示值資料行和分數指標，其與指標資料方格中的指標相同。 選取索引鍵、標籤以及選用的父索引鍵資料行後，您可以選取輸入資料表和資料行以提供計分卡資料。 計分卡資料資料行應可依索引鍵資料行執行篩選。  

1. 從**配置**索引標籤，拖曳**計分卡方格**設計介面，並調整其大小，您想要的方式。

2. 選取**資料** 索引標籤，然後在**資料屬性**窗格下的**金鑰**，選取資料表和資料行篩選。 

3. 在下**標籤**，選取將會顯示標籤的資料行。 索引鍵資料行與標籤資料行可相同。  
  
4. 若要新增計分指標，在**資料行**窗格中，選取**增益分數**。   
  
5. 為計分指標命名，然後選取**選項**設定相同的屬性，您會為資料方格中的標記：  
  
   * 量測計類型
   * 值欄位
   * 比較欄位
   * 值方向
  
6. 若要新增新增值指標，在**資料行**窗格中，選取**增值**。

7. 視需要為值指標命名，從資料表中選擇其來源資料行，然後選取格式化的方式。  

   ![mobile-report-scorecard-grid-data-properties](../../reporting-services/mobile-reports/media/mobile-report-scorecard-grid-data-properties.png)

8. 在設定資料屬性之後,**選擇清單篩選資料表**，選取要篩選的資料表和資料行來篩選。 此資料行需要比對選擇清單之索引鍵資料行中的值。 

如果您在預覽或 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] Web 入口網站中檢視行動報表，並且在計分卡方格中選取值，則會篩選行動報表中的其他視覺效果。

![mobile-report-scorecard-grid](../../reporting-services/mobile-reports/media/mobile-report-scorecard-grid.png)
    
## <a name="set-which-visualizations-are-filtered"></a>設定所篩選的視覺效果  
  
在資料檢視中針對特定輸入按一下選項按鈕，以設定組件庫項目來使用篩選。 切換適當的核取方塊以啟用篩選。  

您可以決定行動報表中行動導覽器將篩選哪些視覺效果︰

1. 選取視覺效果中，選取**資料** 索引標籤，然後在**資料屬性**窗格中，選取**選項**欄位名稱旁邊。

   ![mobile-report-set-selection-list](../../reporting-services/mobile-reports/media/mobile-report-set-selection-list.png)

2. 在下**經過**，選取 [導覽器]。 多個導覽器可以篩選每個視覺效果。
  
## <a name="cascading-filters"></a>階層式篩選   
  
篩選亦可串聯在一起，以讓其中一個項目的選取值篩選第二個項目的可用值。 若要串聯篩選，請如同一般組件庫項目將篩選套用至索引鍵資料行。  

### <a name="see-also"></a>另請參閱 
  
* [Reporting Services 行動報表中的地圖](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)
* [Reporting Services 行動報表中的視覺效果](../../reporting-services/mobile-reports/add-visualizations-to-reporting-services-mobile-reports.md)
* [Reporting Services 行動報表中的量測計](../../reporting-services/mobile-reports/add-gauges-to-mobile-reports-reporting-services.md)
* [Reporting Services 行動報表中的資料格](../../reporting-services/mobile-reports/add-data-grids-to-mobile-reports-reporting-services.md)  

