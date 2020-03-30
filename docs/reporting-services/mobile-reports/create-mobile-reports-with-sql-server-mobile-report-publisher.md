---
title: 使用 SQL Server 行動報表發行工具建立行動報表 | Microsoft Docs
description: 深入了解有各種資料視覺效果，連線到內部部署資料的行動裝置 Reporting Services 行動報表。
ms.date: 12/06/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: a5a8dbf6-4c3a-435d-8188-d6656c32f229
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 51708fc41bb154fcf67ac3a21bd6680c69e2f2c2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "63200547"
---
# <a name="create-mobile-reports-with-sql-server-mobile-report-publisher"></a>使用 SQL Server 行動報表發行工具建立行動報表
深入了解有各種資料視覺效果的 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 行動報表，針對行動裝置最佳化並可連接到內部部署資料。 

>[!NOTE]
>  您需要將儀表板和 KPI 等 Datazen 伺服器內容移轉至 SQL Server[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 伺服器嗎？ 請嘗試 [適用於 Datazen 的 SQL Server 移轉小幫手](https://www.microsoft.com/download/details.aspx?id=53128)。 
 
![SS_MRP_LayoutTabSm](../../reporting-services/media/ss-mrp-layouttabsm.png)  

使用 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)]，您可以快速建立 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 行動報表，針對行動裝置最佳化並有各種其他外型規格。 行動報表具備各種視覺效果，從時間、類別和比較圖表到矩形式樹狀結構圖和自訂的對應。 

* 將行動報表連接到資料來源範圍，包括內部部署 SQL Server 和 Analysis Services 資料。 
* 在設計介面上，使用可調式格線列和格線欄以及根據任何螢幕大小適當縮放的彈性行動報表元素，來配置行動報表。 
* 然後將這些行動報表儲存至 Reporting Service 伺服器，在 iPad、iPhone、Android 手機和平板電腦以及 Windows 10 裝置的瀏覽器或 Power BI 行動裝置應用程式中，檢視報表並與其互動。
  
## <a name="create-ssrsnoversion_md--mobile-reports"></a>建立 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]  行動報表  
  
這些文件會協助您開始。
-  下載 [SQL Server 行動報表發行工具](https://go.microsoft.com/fwlink/?LinkID=733527)  
-  [建立 Reporting Services 行動報表](../../reporting-services/mobile-reports/create-a-reporting-services-mobile-report.md)  
-  [端對端逐步解說︰在 SQL Server Reporting Services 中建立行動報表及 KPI](https://christopherfinlan.com/2015/12/21/how-to-create-mobile-reports-and-kpis-in-sql-server-reporting-services-2016-an-end-to-end-walkthrough/) (Christopher Finlan 的部落格，英文)  
- [設計優先或資料優先](../../reporting-services/mobile-reports/design-first-or-data-first-when-creating-in-reporting-services-mobile-reports.md)：決定要先以模擬的資料來設計報表，或先以您自有的資料開始。  
- [Reporting Services 行動報表的資料](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md)：使用來自共用資料集的資料，或從 Excel 活頁簿準備用於行動報表的資料。
- [Reporting Services 中行動報表和 KPI 的資料重新整理如何運作](https://christopherfinlan.com/2016/02/10/so-refreshinghow-data-refresh-works-with-mobile-reports-and-kpis-in-reporting-services/) (Christopher Finlan 的部落格)：閱讀有關針對共用資料集設定快取的內容，這樣您就能控制資料重新整理的頻率並提升報表的效能。
- [行動報表中的視覺效果](../../reporting-services/mobile-reports/add-visualizations-to-reporting-services-mobile-reports.md)
- [行動報表中的量測計](../../reporting-services/mobile-reports/add-gauges-to-mobile-reports-reporting-services.md)
- [行動報表中的地圖](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)
- 使用公司的色彩和標誌[標示網頁入口網站和行動報表](../../reporting-services/branding-the-web-portal.md)
  
## <a name="ssrs-mobile-reports-in-the-power-bi-mobile-apps"></a>Power BI 行動裝置應用程式中的 SSRS 行動報表

-  在適用於 iOS 和 Android 的 Power BI 行動裝置應用程式中檢視 [Reporting Services 行動報表和 KPI](https://powerbi.microsoft.com/documentation/powerbi-mobile-iphone-kpis-mobile-reports)
-  在適用於 Windows 10 裝置的 Power BI 應用程式中檢視 [Reporting Services 行動報表和 KPI](https://powerbi.microsoft.com/documentation/powerbi-mobile-win10-kpis-mobile-reports/)   

## <a name="see-also"></a>另請參閱  
  
-   [建立、修改及刪除共用資料來源 (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)  
-   [管理共用資料集](../../reporting-services/report-data/manage-shared-datasets.md)  
-  [使用 Reporting Services 中的 KPI](../../reporting-services/working-with-kpis-in-reporting-services.md)  
- [啟用報表伺服器進行 Power BI 行動存取](../../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md)  

  
  

