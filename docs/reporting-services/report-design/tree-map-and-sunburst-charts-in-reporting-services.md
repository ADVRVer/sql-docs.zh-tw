---
title: "Reporting Services 中的樹狀圖與放射環狀圖 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "08/31/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12307c8f-bca7-4d21-8ad5-0c07d819865b
caps.latest.revision: 17
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 16
---
# Reporting Services 中的樹狀圖與放射環狀圖
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 樹狀圖和放射環狀視覺效果是以視覺呈現階層資料的絕佳方式。   本主題是如何新增樹狀圖或放射環狀圖到 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表的概觀。 本主題也包含範例 Adventureworks 查詢，以協助您快速入門。  
  
##  <a name="bkmk_treemap_chart"></a> 樹狀圖  
 ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")  
  
 樹狀圖會將圖表區域分割成矩形，該矩形代表資料階層的不同層級與相對大小。 樹狀圖類似樹上的樹枝，從主幹開始，分割為越來越小的分支。 每個矩形會分成較小的矩形，表示階層中的下一個層級。 最上層的樹狀圖矩形的排列方式是，最大的矩形排列在圖表左上角，最小的矩形在右下角。  在矩形中，更高的下一層級也會從左上到右下排列矩形。  
  
 例如，在以下範例樹狀圖的影像中，Southwest (西南) 的領域最大，而 Germany (德國) 最小。 Southwest (西南) 當中，Road Bikes (公路自行車) 比 Mountain Bikes (登山自行車) 大。  
  
 ![ssrs_treemap_example](../../reporting-services/report-design/media/ssrs-treemap-example.png "ssrs_treemap_example")  
  
### 插入樹狀圖圖表並設定範例 Adventureworks 資料  
 **注意：** 在您新增圖表到報表前，請建立資料來源和資料集。  如需範例資料和範例查詢，請參閱本主題中的 [範例 Adventureworks 資料](#bkmk_sample_data) 章節。  
  
1.  以滑鼠右鍵按一下設計介面，按一下 [插入]，然後按一下 [圖表]。  
  
     選取樹狀圖 ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")。  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  重新調整圖表位置及大小。   若要使用範例資料，5 英吋寬的圖表是不錯的起點。  
  
3.  從範例資料新增下列欄位：  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**值：** LineTotal<br /><br /> **類別群組：** 依以下順序新增它們：<br /><br /> 1) CategoryName<br /><br /> 2) SubcategoryName<br /><br /> **數列群組：** TerritoryName|  
  
4.  若要對樹狀圖的一般形狀最佳化頁面大小，請將圖例位置設定為底部。  
  
5.  若要新增顯示子類別和總金額的工具提示，以滑鼠右鍵按一下 [LineTotal] 然後按一下 [數列屬性]。  
  
     ![ssrs_visualization_seriesproperties](../../reporting-services/report-design/media/ssrs-visualization-seriesproperties.png "ssrs_visualization_seriesproperties")  
  
     將 **Tooltip** 屬性設定如下：  
  
    ```  
    =Fields!SubcategoryName.Value &": " &Format(Sum(Fields!LineTotal.Value),"C")  
    ```  
  
     如需詳細資訊，請參閱 [Show ToolTips on a Series &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md) (在數列上顯示工具提示 (報表產生器及 SSRS))。  
  
6.  將預設圖表標題變更為「按領域分類的銷售量」。  
  
7.  顯示的標籤值數目會受字型大小、整體圖表區域大小，和特定矩形的大小影響。  若要看到更多標籤，將 LineTotal 的 Label font 屬性變更為 10pt，取代預設的 8pt。  
  
 ![搭配回到頁首連結使用的箭頭圖示](../../analysis-services/instances/media/uparrow16x16.png "搭配回到頁首連結使用的箭頭圖示") [本主題內容](#bkmk_top)  
  
##  <a name="bkmk_sunburst_chart"></a> 放射環狀圖表  
 ![ssrs_sunburst_icon](../../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon")  
  
 在放射環狀圖表中，階層會以一系列的圓形呈現，最高層級的階層會在中心，而最低層級的階層會在中心外以環形顯示。  最低層級的階層在環形外部。  
  
 ![ssrs_sunburst_example](../../reporting-services/report-design/media/ssrs-sunburst-example.png "ssrs_sunburst_example")  
  
### 插入放射環狀圖表並設定範例 Adventureworks 資料  
 **注意：** 在您新增圖表到報表前，請建立資料來源和資料集。  如需範例資料和範例查詢，請參閱本主題中的 [範例 Adventureworks 資料](#bkmk_sample_data) 章節。  
  
1.  以滑鼠右鍵按一下設計介面，按一下 [插入]，然後按一下 [圖表]。  
  
     選取放射環狀圖 ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")。  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  重新調整圖表位置及大小。   針對搭配範例資料使用，5 英吋寬的圖表是不錯的起點。  
  
3.  從範例資料新增下列欄位：  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**值：** LineTotal<br /><br /> **類別群組：** 依以下順序新增它們：<br /><br /> 1) CategoryName<br /><br /> 2) SubcategoryName,<br /><br /> 3) SalesReasonName<br /><br /> **數列群組：** TerritoryName。|  
  
4.  若要對放射環狀圖的一般形狀最佳化頁面大小，請將圖例位置設定為底部。  
  
5.  將預設圖表標題變更為「按領域分類的銷售量 (包含銷售原因)」。  
  
6.  |||  
    |-|-|  
    |![ssrs_sunburst_linetotalproperties](../../reporting-services/report-design/media/ssrs-sunburst-linetotalproperties.png "ssrs_sunburst_linetotalproperties")|若要新增類別群組的值到放射環狀圖作為標籤，請設定標籤屬性 **Visible** = true 和 **UseValueAsLabel**=False。<br /><br /> 顯示的標籤值會受字型大小、整體圖表區域大小，和特定矩形的大小影響。  若要看到更多標籤，將 LineTotal 的 Label font 屬性變更為 8pt，取代預設的 10pt。|  
  
7.  如果您想要不同的色彩範圍，請變更圖表的 **Palette** 屬性。  
  
     ![ssrs_visualization_palette](../../reporting-services/report-design/media/ssrs-visualization-palette.png "ssrs_visualization_palette")  
  
 ![搭配回到頁首連結使用的箭頭圖示](../../analysis-services/instances/media/uparrow16x16.png "搭配回到頁首連結使用的箭頭圖示") [本主題內容](#bkmk_top)  
  
##  <a name="bkmk_sample_data"></a> 範例 Adventureworks 資料  
 本節包含範例查詢及在 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]中建立資料來源和資料集的基本步驟。 如果報表已包含資料來源及資料集，您可以略過此章節。  
  
 查詢會傳回 Adventureworks 銷售訂單詳細資料，包含銷售區域、產品類別、產品子類別和銷售原因資料。  
  
1.  **取得資料︰**  
  
     本章節中的查詢是以 Adventureworks 資料庫為基礎，該資料庫可從  [Adventure Works 2014 完整資料庫備份](https://msftdbprodsamples.codeplex.com/releases/view/125550)下載取得。  
  
     如需有關如何安裝該資料庫的詳細資訊，請參閱 [How to install Adventure Works 2014 Sample Databases.pdf](https://msftdbprodsamples.codeplex.com/releases/view/125550)(如何安裝 Adventure Works 2014 範例資料庫.pdf)。  
  
2.  **建立資料來源：**  
  
    1.  在 [報表資料] 窗格中，以右鍵按一下 [資料來源] 然後按一下 [加入資料來源]。  
  
    2.  選取 [使用內嵌於報表中的連接] 。  
  
    3.  選取 [Microsoft SQL Server] 的連接類型。  
  
    4.  輸入您的伺服器與資料庫的連接字串，例如下列連接字串：  
  
        ```  
        Data Source=[server name];Initial Catalog=AdventureWorks2014  
        ```  
  
    5.  最好使用 [測試連接]  按鈕然後按一下 [確定] 來驗證。  
  
     建立資料來源的詳細資訊，請參閱 [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) (加入及驗證資料連接 (報表產生器及 SSRS))。  
  
3.  **建立資料集：**  
  
    -   在 [報表資料] 窗格中，以滑鼠右鍵按一下 [資料集]，然後按一下 [加入資料集]。  
  
    -   選取 [使用內嵌在我的報表中的資料集] 。  
  
    -   選取您在先前的步驟中建立的資料來源。  
  
    -   選取 [文字]  查詢類型，然後將下列查詢複製並貼上到 [查詢:]  文字方塊；  
  
        ```  
        SELECT    Sales.SalesOrderHeader.SalesOrderID, Sales.SalesOrderHeader.OrderDate, Sales.SalesOrderDetail.SalesOrderDetailID, Sales.SalesOrderDetail.ProductID, Sales.SalesOrderDetail.LineTotal,   
                                 Sales.SalesOrderDetail.UnitPrice, Sales.SalesOrderDetail.OrderQty, Production.Product.Name, Production.Product.ProductNumber, Sales.SalesTerritory.TerritoryID, lower(Sales.SalesTerritory.Name) AS TerritoryName,   
                                 Production.ProductSubcategory.Name AS SubcategoryName, Production.ProductCategory.Name AS CategoryName, Sales.SalesReason.SalesReasonID, Sales.SalesReason.Name AS SalesReasonName  
        FROM            Sales.SalesOrderDetail INNER JOIN  
                                 Sales.SalesOrderHeader ON Sales.SalesOrderDetail.SalesOrderID = Sales.SalesOrderHeader.SalesOrderID INNER JOIN  
                                 Production.Product ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID INNER JOIN  
                                 Sales.SalesTerritory ON Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND   
                                 Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID INNER JOIN  
                                 Production.ProductSubcategory ON Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID INNER JOIN  
                                 Production.ProductCategory ON Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID INNER JOIN  
                                 Sales.SalesOrderHeaderSalesReason ON Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID INNER JOIN  
                                 Sales.SalesReason ON Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID  
        ```  
  
    -   按一下 [確定] 。  
  
     如需建立資料集的詳細資訊，請參閱 [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) (建立共用資料集或內嵌資料集 (報表產生器及 SSRS))。  
  
 ![搭配回到頁首連結使用的箭頭圖示](../../analysis-services/instances/media/uparrow16x16.png "搭配回到頁首連結使用的箭頭圖示") [本主題內容](#bkmk_top)  
  
## 請參閱＜  
 [共用資料集設計檢視 &#40;報表產生器&#41;](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
 [在數列上顯示工具提示 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)   
 [教學課程：Power BI 中的樹狀圖](https://support.powerbi.com/knowledgebase/articles/556200-tutorial-treemaps-in-power-bi)   
 [矩形式樹狀結構圖：適用於 Office 的 Microsoft 研究資料視覺效果 App](http://research.microsoft.com/en-us/projects/msrdatavis/treemap.aspx)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]
