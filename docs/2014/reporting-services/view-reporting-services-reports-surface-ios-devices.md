---
title: 在 Microsoft Surface 裝置和 Apple iOS 裝置上檢視 Reporting Services 報表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
caps.latest.revision: 21
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 683a20afc442b7e10a64cac86aa0502c57dabbc0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166319"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a>在 Microsoft Surface 裝置及 Apple iOS 裝置上檢視 Reporting Services 報表
  本文將描述支援 Microsoft Surface 裝置以及具有 Apple iOS 6 與 Apple Safari 之裝置 (例如 iPad) 的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能和工作流程。  
  
## <a name="view-and-interact-with-reports"></a>檢視報表並進行互動  
 開頭[!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]，[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]支援在 Microsoft Surface 裝置以及具有 Apple iOS 6 與 Apple Safari 瀏覽器，例如 iPad 裝置上的報表的檢視和基本互動。 使用 Microsoft Surface 裝置，也可以發行報表。  
  
 ![IPad 桌面](media/videothumbnail.jpg "IPad 桌面")  
在 iPad 上觀看檢視報表的示範。  
  
 您也可以在 Windows Phone 8 裝置上檢視 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表。  
  
 若要使用本主題所描述的功能，請安裝下列其中一個元件：  
  
-   如果是原生模式報表伺服器，請安裝 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 或更新版本。  
  
     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 適用於從下載[Microsoft 下載中心](http://www.microsoft.com/download/details.aspx?id=35575)。  
  
-   針對 SharePoint 模式報表伺服器上，安裝[!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]或更新版本的[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]增益集適用於 SharePoint 產品。  
  
 **若要檢視並與其互動的 iPad 裝置或 Microsoft Surface 裝置上的報表**  
  
1.  請確定您可以連接到報表所在的報表伺服器或 SharePoint 網站。  
  
2.  執行下列其中一項動作來開啟報表。  
  
    -   **從電子郵件啟動：** 所建立的電子郵件[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]訂用帳戶，請點選報表的 URL。 報表將在瀏覽器中開啟。  
  
    -   **從報表伺服器開始：** 上瀏覽目錄[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]報表伺服器，，，然後點選報表名稱開啟報表。  
  
    -   **從 SharePoint 文件庫開始：** 瀏覽至 SharePoint 文件庫，其中包含[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]報表，然後點選 報表名稱。 您就可以檢視報表並進行互動。  
  
        > [!IMPORTANT]  
        >  如果是 iPad，請確定 Safari 的 **[私密瀏覽]** 屬性已關閉。  
  
    -   **SharePoint web 組件：** 如果已將 web 組件加入至 SharePoint 頁面中，您可以檢視[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]報表。  
  
3.  您也可以在您的 Microsoft Surface 裝置上，使用報表管理員來開啟報表。 瀏覽的目錄中[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]報表管理員，，，然後點選報表名稱開啟報表。  
  
    > [!IMPORTANT]  
    >  iPad 不支援在報表管理員中檢視報表。  
  
4.  執行下列操作進行捲動和縮放。  
  
    -   若要捲動報表，請拖曳手指橫過畫面 (上、下、左或右)。 這是撥動手勢。  
  
    -   若要放大，請將兩隻手指放在畫面上，然後分開手指。 若要縮小，請將兩隻手指放在畫面上，然後將手指併攏。 這是捏合手勢。  
  
5.  執行下列動作導覽報表以及與報表互動。  
  
    -   藉由點選加號 (+) 摺疊以及減號 (-) 展開的方式，摺疊和展開報表項目，以及與群組相關聯的資料列和資料行。  
  
    -   藉由點選排序按鈕的方式，在資料表中切換資料列的遞增和遞減順序，或在矩陣中切換資料列及資料行的遞增和遞減順序。 排序按鈕通常位於資料行標頭。  
  
    -   藉由點選報表頂端附近的箭頭按鈕，展開和摺疊參數窗格。  
  
    -   藉由點選參數旁的方塊或控制項，選取參數值。 點選 **[檢視報表]** ，將參數值套用至報表。  
  
    -   藉由點選 **[尋找]** 旁的方塊、輸入搜尋詞彙，然後點選 **[尋找]** 的方式，搜尋報表內容。  
  
    -   藉由點選導覽按鈕，或點選按鈕旁的文字方塊並輸入頁碼的方式，導覽報表頁面。  
  
    -   藉由點選已加入報表項目的超連結導覽至 URL，例如文字方塊、影像、圖表和量測計。  
  
    -   藉由點選 **[匯出下拉式功能表]** 圖示，然後點選檔案格式，匯出報表。  
  
        -   如果您正在 Microsoft Surface 裝置上檢視報表，就可以將報表匯出成下列其中一種格式。  
  
            -   包含報表資料的 XML 檔  
  
            -   CSV (逗號分隔)  
  
            -   PDF  
  
            -   MHTML (網頁封存)  
  
            -   [匯出]  
  
            -   TIFF  
  
            -   Word  
  
        -   如果您正在 iPad 上檢視報表，就可以將報表匯出成 TIFF 或 PDF 檔案。  
  
## <a name="authentication"></a>驗證  
 RSWindowsNTLM 驗證和 RSWindowsBasic 驗證可與[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]原生模式和 iPad。  
  
 一般來說，建議不要在非 https 環境中使用 RSWindowsBasic，因為這種驗證類型不會對傳輸的認證提供機密性。  
  
 如需有關 RSWindowsNTLM 和 RSWindowsBasic 驗證的詳細資訊，請參閱 < [Authentication with Report Server](security/authentication-with-the-report-server.md)。  
  
## <a name="uploading-reports"></a>上傳報表  
 如果您有適當的權限，可透過下列其中一個方法，從 Microsoft Surface 裝置發行報表。  
  
> [!IMPORTANT]  
>  iPad 不支援這些方法。  
  
-   開啟文件庫並點選 **[上傳文件]**，將報表定義檔案 (.rdl) 上傳至 SharePoint 文件庫。  
  
-   開啟報表管理員並點選 **[上傳檔案]**，將報表定義檔案上傳至報表伺服器資料庫。  
  
## <a name="additional-information"></a>其他資訊  
 如需有關[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]和支援的瀏覽器，請參閱：  
  
-   [規劃 Reporting Services 和 Power View 瀏覽器支援&#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)  
  
 如需有關 Microsoft Business Intelligence 和行動裝置的詳細資訊，請參閱下列主題：  
  
-   [行動裝置和 SharePoint 2013 的概觀](http://technet.microsoft.com/library/fp161351\(v=office.15\).aspx)(http://technet.microsoft.com/library/fp161351(v=office.15).aspx)。  
  
-   [支援在 SharePoint 2013 中的行動裝置瀏覽器](http://technet.microsoft.com/library/fp161353\(v=office.15\).aspx)(http://technet.microsoft.com/library/fp161353(v=office.15).aspx)。  
  
-   [Apple iPad 裝置 (SharePoint Server 2010) 上檢視報表和計分卡](http://technet.microsoft.com/library/hh697482.aspx)(http://technet.microsoft.com/library/hh697482.aspx)。  
  
-   [（影片） iPad 上檢視 Reporting Services 報表](http://technet.microsoft.com/sqlserver/jj873792.aspx)(http://technet.microsoft.com/sqlserver/jj873792.aspx)。  
  
-   [Microsoft Surface RT 裝置 （影片） 上檢視 Reporting Services 報表](http://technet.microsoft.com/sqlserver/dn146017)  
  
  
