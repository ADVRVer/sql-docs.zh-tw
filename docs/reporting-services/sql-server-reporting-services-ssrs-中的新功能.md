---
title: "Reporting Services (SSRS) 中的新功能 | Microsoft Docs"
ms.date: "03/14/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "新功能 [Reporting Services]"
  - "Reporting Services, 新功能"
  - "SQL Server Reporting Services, 新功能"
  - "SSRS, 新功能"
ms.assetid: bc909063-6b84-4b3a-80d2-e93fc04b4b9d
caps.latest.revision: 206
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# SQL Server Reporting Services (SSRS) 中的新功能
了解 SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中的新功能。 這會涵蓋主要功能領域，並在發行新的項目時更新。
  
  如需 SQL Server 其他區域之新功能的資訊，請參閱 [SQL Server vNext 中的新功能](../sql-server/what-s-new-in-sql-server-vnext.md)或 [SQL Server 2016 中的新功能](../sql-server/what-s-new-in-sql-server-2016.md)。
  
 **下載** ![download](../analysis-services/media/download.png "download")
 
- 若要下載 SQL Server Reporting Services 中的 Power BI 報表 2017 年 1 月技術預覽，以及 Power BI Desktop 版本 (SQL Server Reporting Services)，請移至 **[Microsoft 下載中心](https://go.microsoft.com/fwlink/?linkid=839351)**。
  
-   若要下載 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]，請前往  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**。  
  
-   有 Azure 帳戶嗎？  接著前往 **[這裡](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016sp1enterprisewindowsserver2016/)**，來加速已安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的虛擬機器。  
  
 ![附註](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "附註") 如需目前的版本資訊，請參閱 [SSRS 中的 Power BI 報表技術預覽 - 版本資訊](../reporting-services/reporting-services-版本資訊.md)或 [SQL Server 2016 版本資訊](../sql-server/sql-server-2016-release-notes.md)。  

## <a name="whats-new-in-the-january-2017-technical-preview-of-power-bi-reports-in-sql-server-reporting-services"></a>SQL Server Reporting Services 中的 Power BI 報表 2017 年 1 月技術預覽的新功能

### <a name="reporting-services-has-a-new-setup-experience"></a>Reporting Services 有全新的安裝體驗

Reporting Services 現已可獨立於 SQL Server 之外安裝。 安裝只需幾個步驟而且更精簡。 過程中會安裝 Reporting Services 的檔案。 您可以針對報表伺服器設定資料庫。 您需要能夠存取您環境中的 SQL Server Database Engine 伺服器。

![ssrs-standalone-setup1](../reporting-services/media/ssrs-standalone-setup1.png)

如需詳細資訊，請參閱[安裝 SQL Server Reporting Services 中的 Power BI 報表 2017 年 1 月技術預覽](Install%20the%20January%202017%20Technical%20Preview%20of%20Power%20BI%20reports%20in%20SQL%20Server%20Reporting%20Services.md)。

### <a name="host-power-bi-reports-within-the-web-portal"></a>在 Web 入口網站中裝載 Power BI 報表

您現在可以將 Power BI Desktop 檔案上傳到 Reporting Services 並直接在 Web 入口網站檢視報表。

![ssrs-powerbi-report-config-render](../reporting-services/media/ssrs-powerbi-report-config-render.png)

您需要下載 Power BI Desktop 版本 (SQL Server Reporting Services)。 預覽版目前僅支援在此 Power BI Desktop 版本中建立的報表。 Power BI Desktop (SQL Server Reporting Services) 可與適用於 Power BI 服務的 Power BI Desktop 並存。 若要下載 Power BI Desktop (SQL Server Reporting Services)，請移至 Microsoft 下載中心。 

目前僅能對 Analysis Services (表格式或多維度) 的即時連線建立 Power BI 報表。 我們計畫在未來的預覽版中，新增對其他資料來源及使用 Power Query 功能的支援。

如需詳細資訊，請參閱 [Reporting Services 中的 Power BI 報表](../reporting-services/power-bi-reports-in-reporting-services.md)。
 
## <a name="whats-new-in-sql-server-2016"></a>SQL Server 2016 的新功能
  
### <a name="reporting-services-includessrswebportal-non-markdowntokenssrswebportal-non-markdownmdmd"></a>Reporting Services [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]  
 有新的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]可用。 這是更新過的新式入口網站，納入了 KPI、行動報表、分頁報表、Excel 和 Power BI Desktop 檔案。 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] 取代舊版中的報表管理員。 您也可以從[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]下載行動報表發行工具和報表產生器，而不需要 ClickOnce 技術。
 
 若要建立行動報表，您將需要 [!INCLUDE[SS_MobileReptPub_Short](../includes/ss-mobilereptpub-short-md.md)]。  
  
 如需[!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]的詳細資訊，請參閱[入口網站 (SSRS 原生模式)](../reporting-services/web-portal-ssrs-native-mode.md)。  
  
 ![ssRSPortal](../reporting-services/media/ssrsportal.png "ssRSPortal")  
 
 #### <a name="custom-branding-for-the-includessrswebportal-non-markdowntokenssrswebportal-non-markdownmdmd"></a>[!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 的自訂商標 
  您可以使用商標套件，以組織的標誌和色彩自訂[!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]。  
  
  如需自訂商標的詳細資訊，請參閱[建立入口網站品牌形象](http://msdn.microsoft.com/zh-tw/6dac97f7-02a6-4711-81a3-e850a6b40bf1)
 
 #### <a name="key-performance-indicators-kpi-in-the-includessrswebportal-non-markdowntokenssrswebportal-non-markdownmdmd"></a>[!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]中的關鍵效能指標 (KPI) 

您可以直接在 [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 中，建立與所在資料夾內容相關的 KPI。 建立 KPI 時，您可以選擇資料集欄位並彙總這些值。 您也可以選取相關內容，以鑽研至更多詳細資料。
  
 ![ssrs-webportal-kpi](../reporting-services/media/ssrs-webportal-kpi.png)
 
 如需詳細資訊，請參閱[使用入口網站中的 KPI](http://msdn.microsoft.com/zh-tw/a28cf500-6d47-4268-a248-04837e7a09eb)
  
 
 ### <a name="mobile-reports"></a>行動報表
 
Reporting Services 行動報表是針對各種外形規格最佳化的專用報表，並為存取行動裝置上報表的使用者提供最佳體驗。 行動報表具備各種視覺效果，從時間、類別和比較圖表，到矩形式樹狀結構圖和自訂地圖。 將行動報表連接到資料來源範圍，包括內部部署 SQL Server Analysis Services 多維度和表格式資料。 在設計介面上，使用可調式格線列和格線欄以及根據任何螢幕大小適當縮放的彈性行動報表元素，來配置行動報表。 然後將這些行動報表儲存至 Reporting Service 伺服器，在 iPad、iPhone、Android 手機及 Windows 10 裝置的瀏覽器或 Power BI 行動裝置應用程式中，檢視報表並與其互動。
  
#### <a name="mobile-report-publisher"></a>行動報表發行工具  
 [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] 可讓您將 SQL Server 行動報表建立並發行到您的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]。  
  
 ![SS_MRP_LayoutTabSmall](../reporting-services/media/ss-mrp-layouttabsm.png "SS_MRP_LayoutTabSmall")  
  
 如需詳細資訊，請參閱[使用 SQL Server 行動報表發行工具建立行動報表](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)。  
  
#### <a name="sql-server-mobile-reports-hosted-in-reporting-services-available-in-power-bi-mobile-app"></a>裝載於 Reporting Services 的 SQL Server 行動報表可在 Power BI Mobile 應用程式中使用  
 iPad 和 iPhone 上適用於 iOS 的 Power BI 行動裝置應用程式現在可以顯示裝載於本機報表伺服器的 SQL Server 行動報表。  
  
 ![SS_MRP_iPad_HomeSm](../reporting-services/media/ss-mrp-ipad-homesm.png "SS_MRP_iPad_HomeSm")  
  
 根據預設，您必須進行幾項組態變更才能連接。 如需如何允許 Power BI Mobile 應用程式連接到報表伺服器的詳細資訊，請參閱 [Enable a report server for Power BI Mobile access](../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md)。
  
### <a name="support-of-sharepoint-mode-and-sharepoint-2016"></a>支援 SharePoint 模式和 SharePoint 2016 模式。  
 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 支援與 SharePoint 2013 和 SharePoint 2016 整合。
 
如需詳細資訊，請參閱：  
  
-   [支援的 SharePoint 和 Reporting Services 伺服器與增益集的組合 &#40;SQL Server 2016&#41;](../reporting-services/install-windows/supported combinations of sharepoint and reporting services server.md)  
  
-   [尋找適用於 SharePoint 產品之 Reporting Services 增益集的位置](../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [安裝 Reporting Services SharePoint 模式](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  

### <a name="microsoft-net-framework-4-support"></a>Microsoft .NET Framework 4 支援  
 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]支援 Microsoft .NET Framework 4 的目前版本。 其中包括 4.0 和 4.5.1 版。 如果未安裝任何 .Net Framework 4.x 版本， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程式會在功能安裝步驟安裝 .NET 4.0。  

### <a name="report-improvements"></a>報表改進

**HTML 5 轉譯引擎**：新的 HTML5 轉譯引擎以新式 Web「完整」標準模式及新式瀏覽器為目標。  新的轉譯引擎不再依賴幾種舊瀏覽器使用的 quirks 模式。
  
 如需瀏覽器支援的詳細資訊，請參閱 [Reporting Services 和 Power View 的瀏覽器支援](../reporting-services/browser-support-for-reporting-services-and-power-view.md)。  

**新式分頁報表：** 使用樣式新穎的圖表、量測計、地圖和其他資料視覺效果，設計美觀的新式分頁報表。
  
**樹狀圖和放射環狀圖**：使用樹狀圖 ![ssrs_treemap_icon](../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon") 和放射環狀圖 ![ssrs_sunburst_icon](../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon") 加強您的報表，這些圖表適合顯示階層式資料。 如需詳細資訊，請參閱 [Tree Map and Sunburst Charts in Reporting Services](../reporting-services/report-design/tree-map-and-sunburst-charts-in-reporting-services.md)。  

**報表內嵌：** 您現在可以使用 iframe 及 URL 參數，將行動和分頁報表內嵌到其他網頁和應用程式中。  

**將報表項目釘選到 Power BI 儀表板**：當您在[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]中檢視報表時，可以選取報表項目，並將其釘選到 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 儀表板。   可釘選的項目包括圖表、量測計面板、地圖和影像。 您可以 **(1)** 選取包含您要釘選之目的地儀表板的群組，**(2)** 選取您也要釘選項目的儀表板，以及 **(3)** 選取您要在儀表板中更新磚的頻率。   ![附註](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "附註") 重新整理由 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 訂閱管理，而釘選項目之後，您可以編輯訂閱和設定不同的重新整理排程。  
  
 ![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png) 
  
 如需詳細資訊，請參閱 [Power BI 報表伺服器整合 &#40;組態管理員&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md) 和[將 Reporting Services 項目釘選到 Power BI 儀表板](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)。  
 
 **PowerPoint 轉譯及匯出**：Microsoft PowerPoint (PPTX) 格式是新的 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 轉譯延伸模組。 您可以使用 PPTX 格式從下列常用應用程式匯出報表：報表產生器、報表設計師 (在 SSDT 中) 和[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]。 如需範例，下圖顯示了[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]的匯出功能表。 
  
 ![ssrs-export-powerpoint](../reporting-services/media/ssrs-export-powerpoint.png) 
  
 您也可以對訂閱輸出選取 PPTX 格式，並使用報表伺服器 URL 存取來轉譯及匯出報表。 例如，您瀏覽器中的以下 URL 命令會從報表伺服器的具名執行個體匯出報表。  
  
```  
http://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 如需詳細資訊，請參閱 [Export a Report Using URL Access](../reporting-services/export-a-report-using-url-access.md)。  
 
 **PDF 在遠端列印取代 ActiveX**：新式 PDF 體驗已取代報表檢視器工具列 ActiveX 列印體驗，前者可跨支援的瀏覽器矩陣運作，包括 Microsoft Edge。 不再需要下載任何 ActiveX 控制項！ 根據您使用的瀏覽器以及已安裝的 PDF 檢視應用程式和服務，[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 會開啟 [列印] 對話方塊以列印您的報表，或提示您下載報表的 .PDF 檔案。  您身為系統管理員，仍可以從 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]停用用戶端列印。 如需詳細資訊，請參閱[啟用和停用 Reporting Services 的用戶端列印](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)。

![ssrs-pdf-printing](../reporting-services/media/ssrs-pdf-printing.png)

### <a name="subscription-improvements"></a>訂閱功能改進  
 
|功能|支援的伺服器模式|  
|-------------|---------------------------|  
|**啟用和停用訂閱**。 新的使用者介面選項可快速停用及啟用訂閱。 停用的訂閱會維持其中的其他組態屬性，例如排程，並且可以輕鬆啟用。<br /><br /> ![ssrs-enable-disable-subscriptions](../reporting-services/media/ssrs-enable-disable-subscriptions.png)<br /><br /> 如需詳細資訊，請參閱 [Disable or Pause Report and Subscription Processing](../reporting-services/subscriptions/disable-or-pause-report-and-subscription-processing.md)。|原生模式|  
|**訂閱描述**。 您現在可以在建立新訂閱時，在訂閱屬性中加入報表的描述。 該描述會加到訂閱摘要頁面上。|SharePoint 與原生模式|  
|**變更訂閱擁有者**。 加強的使用者介面可快速變更訂閱的擁有者。 舊版 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 可讓系統管理員使用指令碼變更訂閱擁有者。 從 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] 版本開始，您可以使用使用者介面或指令碼來變更訂閱擁有者。 有使用者離開或在組織中變更角色時，便需要進行變更訂閱擁有者這項一般管理工作。|SharePoint 與原生模式|  
|**檔案共用訂閱的共用認證**。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 檔案共用訂閱現在同時存有兩個工作流程：<br /><br /> 您的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 系統管理員可以使用此版本的新功能，設定可供一到多個訂閱使用的單一檔案共用帳戶。 檔案共用帳戶是在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 原生模式組態管理員的 [指定檔案共用帳戶] 中設定，而使用者接著要在訂閱組態頁面上選取 [使用檔案共用帳戶] 。<br /><br /> 針對目的檔案共用，使用特定認證設定個別訂閱。<br /><br /> 您也可以混用兩種方法，讓某些檔案共用訂閱使用中央檔案共用帳戶，而其他訂閱則使用特定認證。|原生模式|  

### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
 SSDT 的新版本包括 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 的專案範本：[報表伺服器專案精靈] 與 [報表伺服器專案]。 如需下載 SSDT 的相關資訊，請參閱 [SQL Server Data Tools for Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkId=827542)(適用於 Visual Studio 2015 的 SQL Server Data Tools)。  

### <a name="report-builder-improvements"></a>報表產生器改進

**新的報表產生器使用者介面**：核心 [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] 使用者介面現在透過簡化的 UI 元素，具備了新式外觀及操作。  
  
|||  
|-|-|  
|新增|Previous|  
|![ssrs_rbfacelift_new](../reporting-services/media/ssrs-rbfacelift-new.png "ssrs_rbfacelift_new")|![ssrs_rbfacelift_old](../reporting-services/media/ssrs-rbfacelift-old.png "ssrs_rbfacelift_old")|  

**自訂參數窗格**：您現在可以自訂參數窗格。 使用報表產生器中的設計界面，您可以將參數拖曳到參數窗格中的特定資料行及資料列。 您可以新增及移除資料行以變更窗格配置。   如需詳細資訊，請參閱[自訂報表中的參數窗格 &#40;報表產生器&#41;](../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md)。  
  
 ![Parameter list in Report Data pane and in parameters pane](../reporting-services/media/ssrs-customizeparameter-parameterlist-reportdatapane.png "Parameter list in Report Data pane and in parameters pane")  

  
**高 DPI 支援**：[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的 [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] 支援高 DPI (每英吋點數) 縮放比例及裝置。  如需高 DPI 的詳細資訊，請參閱下列主題：  
  
-   [Windows 8.1 DPI 縮放比例功能加強 (英文)](https://blogs.windows.com/windowsexperience/2013/07/15/windows-8-1-dpi-scaling-enhancements/)  
  
-   [高 DPI 與 Windows 8.1](http://technet.microsoft.com/library/dn528848.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 的新功能](http://msdn.microsoft.com/zh-tw/aa69c299-b8f4-4969-86d8-b3292fe13f08)  
 [SSRS 中的 Power BI 報表技術預覽 - 版本資訊](../reporting-services/reporting-services-版本資訊.md)  
 [SQL Server 2016 版本資訊](../sql-server/sql-server-2016-release-notes.md)   
 [回溯相容性](http://msdn.microsoft.com/zh-tw/675b0e0e-cfee-4790-9675-80fc3ea6d30f)   
 [SQL Server 2016 版本支援的 Reporting Services 功能](http://msdn.microsoft.com/zh-tw/39f03d2d-6e48-4b34-a9d3-07f86313b937)   
 [升級和移轉 Reporting Services](../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
 [Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-ssrs.md)  
  
  