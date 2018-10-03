---
title: 比較報表檢視器中的連線模式報表在報表檢視器 (SharePoint 模式的 Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: a230a9bb-6046-401f-b5e5-53ff6edf2264
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cbae778b06c90f1e18cb5e45119a09e25d634738
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165308"
---
# <a name="local-mode-vs-connected-mode-reports-in-the-report-viewer-reporting-services-in-sharepoint-mode"></a>比較報表檢視器中的本機模式與連接模式報表 (SharePoint 模式的 Reporting Services)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表可以設定為執行中*本機模式*或是*連線的模式*，以運用[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]報表伺服器。 而是，當資料延伸模組支援本機模式報表時，您可以使用報表檢視器直接從 SharePoint 轉譯報表。 這種方法稱為 *「本機模式」*(Local Mode)。 在舊版[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]，在 SharePoint 伺服器陣列所需連接至[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]報表伺服器設定為 SharePoint 模式讓報表檢視器控制項可以呈現報表。 此方法稱為 *「遠端模式」* (Remote Mode) 或 *「連接模式」*(Connected Mode)。  
  
 在 *本機模式*沒有任何[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]報表伺服器。 您必須安裝[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]適用於 SharePoint 產品，但不是增益集[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]則需要報表伺服器。 在本機模式中，使用者可以檢視報表，但是無法存取伺服器端的功能 (例如訂閱和資料警示)。  
  
||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 模式|  
  
 **本主題內容：**  
  
-   [本機模式與連接模式及支援的延伸模組](#bkmk_local_vs_connected)  
  
-   [設定 SharePoint 2013 的本機模式和 Access Services](#bkmk_local_mode_sharepoint2013)  
  
-   [設定 SharePoint 2010 的本機模式報表](#bkmk_local_mode_sharepoint2010)  
  
##  <a name="bkmk_local_vs_connected"></a> 本機模式與連接模式及支援的延伸模組  
 **本機模式：** 當您具有支援本機模式的資料延伸模組時，報表檢視器會直接從 SharePoint 呈現報表。 在 *本機模式*沒有任何[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]報表伺服器。 您必須安裝[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]適用於 SharePoint 產品，但不是增益集[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]則需要報表伺服器。 在本機模式中，使用者可以檢視報表，但是 **無法** 存取伺服器端的功能 (例如，訂閱和資料警示)。  
  
 **連接的模式**，也稱為*遠端模式*需要[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]在 SharePoint 模式中，連接到 SharePoint 伺服器陣列，讓報表檢視器控制項可以呈現報表的報表伺服器...  
  
 下面是支援本機模式報表的資料處理延伸模組清單：  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Access 2010 報表延伸模組。 如需 Access Services 的詳細資訊，請參閱 [將 Access Services 與 SQL Reporting Services 配合使用：安裝 SQL Server 2008 R2 Reporting Services 增益集 (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=192686)。  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 清單資料延伸模組。 如需有關 SharePoint 清單資料延伸模組的詳細資訊，請參閱 < [Reporting Services 所支援的資料來源&#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
 您也可以部署自訂資料處理延伸模組來支援本機模式。 如需詳細資訊，請參閱 [Implementing a Data Processing Extension](extensions/data-processing/implementing-a-data-processing-extension.md)。  
  
 本機模式支援轉譯具有 .rsds 檔案中之內嵌資料來源或共用資料來源的報表。 不過，您無法管理報表或其相關聯的資料來源。 如果您嘗試這樣做，將會收到在本機模式不支援這項動作的錯誤。 在 SharePoint 網站中管理資料來源，只有在連接模式下才支援。  
  
> [!NOTE]  
>  就如同舊版一樣，您無法在 .rsds 檔案中內嵌使用者名稱及密碼。  
  
##  <a name="bkmk_local_mode_sharepoint2013"></a> 設定 SharePoint 2013 的本機模式和 Access Services  
 您可以設定 SharePoint 2013 伺服器陣列支援現有 Access 2010 Web 資料庫和 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 本機模式。 如需詳細資訊，請參閱 [安裝及設定 SharePoint Server 2013 中 Web 資料庫的 Access Services 2010](http://technet.microsoft.com/library/ee748653\(office.15\).aspx)。  
  
 您無法為 SharePoint 2013 建立新的 Access Web 資料庫。 Access 2013 會使用您在 Access 中建立的新資料庫類型 *Access Web App* ，然後在 Web 瀏覽器中做為 SharePoint 應用程式使用並與其他人共用。  
  
 如需詳細資訊，請參閱下列內容。  
  
-   [Access 2013 的新功能](http://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) (http://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx)。  
  
-   [Access 應用程式的基本工作](http://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) (http://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500)。  
  
##  <a name="bkmk_local_mode_sharepoint2010"></a> 設定 SharePoint 2010 的本機模式報表  
 本機模式需要 ASP.NET 工作階段狀態。 安裝 Access Services 就會啟用 ASP.Net 工作階段狀態。 您也可以使用 PowerShell 來啟用。  
  
1.  開啟 SharePoint 2010 管理命令介面。  
  
2.  輸入以下命令：  
  
    ```  
    - Enable-SPSessionStateService  
    ```  
  
3.  出現提示時，請輸入資料庫的名稱。  
  
4.  執行 IIS 重設。  
  
 如需詳細資訊，請參閱 [將 Access Services 與 SQL Reporting Services 配合使用：安裝 SQL Server 2008 R2 Reporting Services 增益集 (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=192686) 和 [Enable-SPSessionStateService](http://technet.microsoft.com/library/ff607857\(v=office.15\).aspx)。  
  
## <a name="connected-mode"></a>「連接模式」  
 如需使用 ADS 延伸模組搭配最新資訊[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]連線的模式，請參閱[Access Services 報表，SharePoint 網站中顯示錯誤中的資料延伸模組 'ADS'](http://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx)。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 所支援的資料來源&#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
