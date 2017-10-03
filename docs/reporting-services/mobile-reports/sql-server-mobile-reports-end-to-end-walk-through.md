---
title: "SQL Server 行動報表： 端對端逐步解說 |Microsoft 文件"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e198575e-b154-4342-b944-2bf19ec49bfd
caps.latest.revision: 14
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: ded9d996ffff02c0fc5c239f5dd14d1a6c756bb6
ms.contentlocale: zh-tw
ms.lasthandoff: 09/27/2017

---
# <a name="sql-server-mobile-reports-end-to-end-walk-through"></a>SQL Server 行動報表： 端對端逐步解說
逐步解說在 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] 入口網站透過 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 建立適用於任何螢幕大小的行動報表，並在 Power BI 行動應用程式中檢視它們。

您可以在可調整格線列和欄，並具有彈性的行動報表元素的設計介面上，建立行動報表。 連接到各種不同的內部部署資料來源，或上傳 Excel 活頁簿來建立行動報表。 然後將您的報表儲存到 [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 入口網站，並在瀏覽器中或者 Power BI 行動應用程式中檢視。  
  
本文將逐步引導您完成︰   
  
- 在 [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 入口網站上建立共用資料來源和資料集，並使用 AdventureWorks 資料庫做為範例資料來源。  
- 在 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]中建立 Reporting Services 行動報表  
- 將行動報表發佈至 [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 入口網站。  
- 在 Power BI 行動應用程式中檢視行動報表。  
  
## <a name="before-we-start"></a>開始之前  
若要跟著做，您會需要這些產品︰  
  
* 若要建立資料來源和 Kpi，並將資料集和行動報表發行，您需要存取 [！包含[ssRSCurrent_md](../install-windows/install-reporting-services-native-mode-report-server.md)。  
* 若要[建立共用資料集](../install-windows/install-report-builder.md)。  
* 若要建立行動報表， [請安裝 SQL Server 行動報表發行工具](http://go.microsoft.com/fwlink/?LinkId=717766)。  
* [AdventureWorks 範例資料庫和指令碼](http://msftdbprodsamples.codeplex.com/)。  
*  OR: World Wide Importers 範例資料庫，可從[Microsoft SQL Server Samples](../../sample/microsoft-sql-server-samples.md)頁面。
* 若要檢視結果︰ 
  *   [註冊 Power BI 服務](http://go.microsoft.com/fwlink/?LinkID=513879) ，並且
  *  [下載 Power BI 行動應用程式](https://powerbi.microsoft.com/en-us/documentation/powerbi-power-bi-apps-for-mobile-devices/) 到您的行動裝置：iOS、Android 手機或 Windows 10 裝置。  

  
## <a name="create-a-shared-data-source"></a>建立共用資料來源  
  
您可以從 Reporting Services 支援的任何資料來源，為您的行動報表建立共用資料來源。 請參閱[支援的資料來源清單](../report-data/data-sources-supported-by-reporting-services-ssrs.md)。  
  
1. 從您[!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)]web 入口網站中，按一下**新增** > **資料來源**。  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
3. 輸入您的資料來源資訊 >**確定**。  
  
    根據預設，資料來源不會顯示在入口網站中。    
   
5. 若要檢視資料來源，請按一下**顯示** > **資料來源**。  
  
   ![PBI_SSMRP_DisplayDataSources](../../reporting-services/mobile-reports/media/pbi-ssmrp-displaydatasources.png)  
   
6. 現在您可以在 [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 入口網站中看到資料來源。  
  
   ![PBI_SSMRP_PortlDataSource](../../reporting-services/mobile-reports/media/pbi-ssmrp-portldatasource.png)  
  
深入了解 [Reporting Services 中的共用資料來源](../report-data/create-modify-and-delete-shared-data-sources-ssrs.md)。  
   
## <a name="shared-dataset">建立共用資料集</a>  
  
使用現有的 [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 用戶端工具 (例如 [!INCLUDE[ssBIDevStudioFull_md](../../includes/ssbidevstudiofull-md.md)]中的「報表設計師」) 建立共用資料集。  本逐步解說使用 [!INCLUDE[PRODUCT_NAME](../../includes/ssrbnoversion.md)]。 [安裝報表產生器](https://msdn.microsoft.com/library/ff519551.aspx)，或從您的入口網站啟動它。 您將建立三個資料集，分別針對：KPI 值、KPI 趨勢，以及 Reporting Services 行動報表 (含有更多欄位)。     
  
1. 從您[!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)]web 入口網站中，按一下**新增** > **分頁報表**啟動[!INCLUDE[PRODUCT_NAME](../../includes/ssrbnoversion.md)]。  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)   
2. 按一下**新的資料集**。  
  
   ![PBI_SSMRP_RBNewDataset](../../reporting-services/mobile-reports/media/pbi-ssmrp-rbnewdataset.png)  
   
3. 按一下**瀏覽其他資料來源**。  
   
4. 在 [名稱] 欄位中，以下列格式輸入您儲存資料來源的伺服器名稱：   
   
   名稱：http://*localhost*/ReportServer  
   類型的項目：資料來源 (*.rsds)  
   
5. 按一下**開啟**，並瀏覽至您建立該伺服器的資料來源。  
   
6. 選取您的資料來源，然後按一下**開啟**一次。    
  
7. 在 [!INCLUDE[PRODUCT_NAME](../../includes/ssrbnoversion.md)]中設計您的資料集。  
  
   ![PBI_SSMRP_RB_QueryDesignr600](../../reporting-services/mobile-reports/media/pbi-ssmrp-rb-querydesignr600.png)  
   
8. 完成時，請將資料集儲存到 [!INCLUDE[PRODUCT_NAME](../../includes/ssrs.md)] 報表伺服器。    
   
現在您可以使用該資料集做為您的 KPI 和行動報表的基礎。  您可以針對相同的資料來源建立多個資料集。 而且您可以針對這些共用資料集建立多個 KPI 和行動報表。   
  
## <a name="create-KPI">建立 KPI</a>  
您可以直接在 [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 入口網站中建立 KPI。    
  
1. 在 web 入口網站右上角，按一下**新增** > **新的 KPI**。   
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
      
   在 KPI 建立畫面中，您可以手動輸入值，或使用共用資料集。    
2. 變更**值**從**手動設定**至**資料集欄位**。  
   
   ![PBI_SSMRP_KPI_DatasetField](../../reporting-services/mobile-reports/media/pbi-ssmrp-kpi-datasetfield.png)  
   
3. 按一下省略符號 (**...**) 中**挑選資料集欄位**方塊，然後從上一個步驟中選取的資料集。  
   
   ![PBI_SSMRP_KPIPickDataset](../../reporting-services/mobile-reports/media/pbi-ssmrp-kpipickdataset.png)  
   
4. 選擇資料集中的欄位。    
   
   ![PBI_SSMRP_KPIPickField](../../reporting-services/mobile-reports/media/pbi-ssmrp-kpipickfield.png)  
     
5. 選擇您想要的彙總。 KPI 只能顯示一個數字，因此欄位將會彙總以顯示該數字。

   ![reporting-services-kpi-pick-aggregation](../../reporting-services/mobile-reports/media/reporting-services-kpi-pick-aggregation.png)

6. 按一下 **[確定]**。

7. 在**趨勢集**方塊中，按一下**資料集趨勢**。  
  
6. 在**挑選資料集趨勢**方塊中，按一下省略符號 (**...**)  
   
7. 選取欄位，並按一下**確定**。  

   ![PBI_SSMRP_KPIPickTrend](../../reporting-services/mobile-reports/media/pbi-ssmrp-kpipicktrend.png)  
  
8. 指定您的 KPI 的名稱並選取視覺效果類型，然後按一下**建立**。   
  
   KPI 會出現在 [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 入口網站。  
   
    ![PBI_SSMRP_NewKPI](../../reporting-services/mobile-reports/media/pbi-ssmrp-newkpi.png)  
    
## <a name="create-mobile-report">建立 Reporting Services 行動報表</a>  
   
若要建立 Reporting Services 行動報表， [請安裝 SQL Server 行動報表發行工具](http://go.microsoft.com/fwlink/?LinkId=717766)，或從 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 入口網站啟動它。 

當您第一次開啟 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]時，您會看到一個空白畫布，您可以在其中建立您的行動報表。 您可以先從建立視覺效果開始，或是以您的資料來開始。 如果您先建立視覺效果， [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] 會自動產生繫結至報表的模擬資料，並在您變更視覺選取區時做出動態變更。 請您試試看。   
  
## <a name="start-with-the-visuals"></a>開始使用視覺效果  
  
1. 從您[!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)]web 入口網站中，按一下**新增** > **行動報表**啟動[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]。  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)

   [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] 會開啟到主要的配置方格。  
  
2. 在**配置**索引標籤上，捲動到 [圖表] 區段。  
  
   ![PBI_SSMRP_LayoutTabCharts2](../../reporting-services/mobile-reports/media/pbi-ssmrp-layouttabcharts2.png)  
  
2. 拖曳**樹狀圖**方格中，並使其三個資料行寬和高的三個資料列拖曳右下角。  
  
   ![PBI_SSMRP_TreeMap](../../reporting-services/mobile-reports/media/pbi-ssmrp-treemap.png)  
  
3. 您可以在底部查看其視覺屬性。 您可能要橫向捲動才能看到全部的視覺屬性。   
  
   ![PBI_SSMRP_TreeMapVisProps](../../reporting-services/mobile-reports/media/pbi-ssmrp-treemapvisprops.png)  
  
4. 選取樹狀目錄中的地圖視覺效果，然後選取 [**資料**] 索引標籤中的左上角。   
  
   現在，您會看到 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] 所產生的模擬欄位和值，並能在樹狀圖中查看大小與色彩代表的意義。  
  
   ![PBI_SSMRP_TreeMapDataProps](../../reporting-services/mobile-reports/media/pbi-ssmrp-treemapdataprops.png)  
  
6. 按一下**配置** 索引標籤。  
  
7. 按一下樹狀圖右上角的 [選項] 齒輪 ![PBI_SSMRP_Cog](../../reporting-services/mobile-reports/media/pbi-ssmrp-cog.png) 以檢視它包含的功能表。   
  
   ![PBI_SSMRP_OptionsWheel](../../reporting-services/mobile-reports/media/pbi-ssmrp-optionswheel.png)  
  
8. 按一下滾輪中間的箭號以關閉它。  
  
## <a name="add-your-own-data"></a>新增您自己的資料  
  
1. 切換至**資料** 索引標籤。    
   
2. 新增您自己的資料，請按一下**加入資料**在右上角，然後瀏覽至您的資料。    
  
3. 您可以使用本機 Excel 活頁簿中的資料，但是在此案例中，資料是來自您 [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 入口網站上的共用資料集。 您會看到「已新增伺服器」訊息。  
  
4. 選取該伺服器，然後選取您所建立的資料集。  
   
3. 回到上**資料**索引標籤的**資料屬性**窗格變更**大小代表**，**色彩都代表**，與其他屬性，以您自己的資料中的欄位。 
   
   *  **大小代表**，**色彩都代表**，和**自訂中心值**一定要有數值的欄位。 
   *  **Group By**是類別，因此它是一個文字欄位。
   
   ![ssrs-mobile-report-data-properties](../../reporting-services/mobile-reports/media/ssrs-mobile-report-data-properties.png)
   
6. 選取**預覽**若要查看對應的樹狀目錄更新您的資料。  

## <a name="add-a-gauge-to-your-mobile-report"></a>將量測計新增到行動報表

讓我們使用相同的資料集，並新增量測計以查看年初至今的銷售額，與去年的銷售額相比的狀況。

1. 在 [配置] 索引標籤上，將半個同心圓拖曳至畫布。 將它放在樹狀圖下，並拖曳右下角讓它為三個正方形寬乘以兩個正方形高。 

2. 同樣地，一開始也會使用模擬的資料。 

   請注意，在**視覺屬性**，根據預設**數值愈高愈好**，而**差異標籤**是**目標百分比**。 它有預設**範圍停駐點**您可以變更，但現在沒問題。

   ![ssrs-mobile-report-donut-visual-properties](../../reporting-services/mobile-reports/media/ssrs-mobile-report-donut-visual-properties.png)
   
3. 在**資料**索引標籤上，選取與您資料的資料表並選取**主要值**及您想要比較中的欄位**比較值**。

4. 您可以選擇不同的彙總為一個數字的**主要值**，另一個用於**比較值**。 根據預設，它會是總和。

   ![ssrs-mobile-report-donut-sum](../../reporting-services/mobile-reports/media/ssrs-mobile-report-donut-sum.png)

5. 選取**預覽**來查看它的外觀。 

   ![ssrs-mobile-report-donut-preview](../../reporting-services/mobile-reports/media/ssrs-mobile-report-donut-preview.png)

## <a name="add-a-selection-list-as-a-filter"></a>將選擇清單新增為篩選條件

選擇清單就像是 Power BI 和 Excel 中的交叉分析篩選器。 我們可以新增一個以篩選行動報表中的其他視覺效果。

1. 在**配置**索引標籤，將選取項目清單拖曳至右邊的樹狀目錄對應，然後拖曳右下角，使其寬度與高度畫布，五個平方兩格。 

   ![ssrs-mobile-report-selection-list](../../reporting-services/mobile-reports/media/ssrs-mobile-report-selection-list.png)

2. 在**資料**索引標籤上，**資料屬性**，將**金鑰**和**標籤**至您想要篩選的資料中的欄位。

   ![ssrs-mobile-report-selection-list-data-properties](../../reporting-services/mobile-reports/media/ssrs-mobile-report-selection-list-data-properties.png)
   
## <a name="create-a-mobile-report-for-phones"></a>針對手機建立行動報表  
  
您在主要的配置上建立視覺效果之後，便可以使用一個專為手機使用者最佳化的配置建立行動報表。    
  
1. 按一下右上角的 畫布圖示 >**電話**。  
  
2. 在 [配置] 索引標籤上**控制項執行個體**，您會看到您已建立的兩個圖表。   
  
3. 將樹狀圖拖曳到手機畫布，並使它為四個資料行寬以及三個資料列高。  
  

## <a name="save-your-mobile-report"></a>儲存您的行動報表  
您可以將您的報表儲存在本機，或儲存到 [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 入口網站。 如果您將報表儲存在本機， [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] 會利用快取資料儲存它，讓您可以開啟它並繼續使用。 但您將無法在行動裝置上檢視它。   
  
1. 按一下左上角的儲存圖示。   
   
2. 若要與他人分享，並檢視行動裝置上，按一下**儲存到伺服器**。  
  
3. 在伺服器上，瀏覽至您想要儲存行動報表的資料夾。  
  
4. 按一下**選擇資料夾** > **儲存**。  
  
   您會收到確認已儲存報表的訊息。  
    
   儲存之後，您可以回到入口網站並查看您的行動報表縮圖。   
    
5. 點選縮圖以在入口網站中查看報表。  
  
## <a name="view-your-report-on-the-web-portal"></a>在入口網站上檢視您的報表

  
## <a name="view-your-report-on-a-mobile-device"></a>在行動裝置上檢視您的報表   
  
若要檢視您的 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 報表，您必須先︰

*  [註冊 Power BI 服務](http://go.microsoft.com/fwlink/?LinkID=513879)(如果您還沒有帳戶)。
*  [下載 Power BI 行動應用程式](https://powerbi.microsoft.com/en-us/documentation/powerbi-power-bi-apps-for-mobile-devices/) 到您的行動裝置。  

### <a name="view-your-mobile-report"></a>檢視您的行動報表
  
1.  在您的行動裝置上開啟並登入 Power BI 應用程式。  
    
2.  若要檢視您的 Reporting Services 行動報表和 Kpi，請點選**Reporting Services**。  
![PBI_iPad_GetStartedSm](../../reporting-services/mobile-reports/media/pbi-ipad-getstartedsm.png)  
  
3. 點選選項圖示![PBI_iPad_OptionsIcon](../../reporting-services/mobile-reports/media/pbi-ipad-optionsicon.png)在左上角，然後點選**連接到伺服器**。  
  
   ![PBI_iPad_SSMRP_ConnectCrop](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-connectcrop.png)  
  
4. 指定伺服器的名稱，並填寫伺服器位址以及您的電子郵件地址和密碼，格式如下︰  
  
   ![PBI_iPad_SSMRP_ConnectContoso](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-connectcontoso.png)   
  
5.  現在您會在左側導覽列中看到伺服器。  
  
    ![PBI_iPad_SSMRP_LeftNavBiggr](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-leftnavbiggr.png)  
      
>**秘訣**：點選選項圖示 ![PBI_iPad_OptionsIcon](../../reporting-services/mobile-reports/media/pbi-ipad-optionsicon.png) 可隨時於您在 Reporting Services 入口網站中的 Reporting Services 行動報表，以及在 Power BI 服務中的儀表板之間切換。   
  
## <a name="view-kpis-and-mobile-reports-in-the-power-bi-app"></a>在 Power BI 應用程式中檢視 KPI 和行動報表  
  
點選**Kpi**或**行動報表** 索引標籤。   
  
![PBI_iPad_SSMRP_Portal](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-portal.png)  
  
- 點選 KPI 以在聚焦模式中查看它。  
  
    ![PBI_iPad_SSMRP_Tile](../../reporting-services/mobile-reports/media/pbi-ipad-ssmrp-tile.png)  
  
- 點選行動報表以在 Power BI 應用程式中開啟它並與之互動。  
  
KPI 與行動報表會顯示於和 Reporting Services 入口網站上相同資料夾中。   
  
### <a name="see-also"></a>另請參閱  
 
-  [在 (Power BI for iOS) iPad 應用程式中檢視 Reporting Services 行動報表和 KPI](https://powerbi.microsoft.com/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  
-  [在 iPhone 應用程式 (Power BI for iOS) 中檢視 Reporting Services 行動報表和 KPI](https://powerbi.microsoft.com/documentation/powerbi-mobile-iphone-kpis-mobile-reports)  
-  [在 Power BI 的 Android 應用程式中檢視 Reporting Services 行動報表和 KPI](https://powerbi.microsoft.com/documentation/powerbi-mobile-android-kpis-mobile-reports)
-  [在 Power BI 的 Windows 10 行動裝置應用程式中檢視 Reporting Services 行動報表和 KPI](https://powerbi.microsoft.com/documentation/powerbi-mobile-win10-kpis-mobile-reports/)    
  
   


