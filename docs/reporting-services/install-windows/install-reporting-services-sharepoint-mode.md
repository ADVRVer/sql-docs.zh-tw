---
title: "安裝 Reporting Services SharePoint 模式 |Microsoft 文件"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b2c77f21304b04b5349691b6c464026fe944a4eb
ms.contentlocale: zh-tw
ms.lasthandoff: 06/13/2017

---
# <a name="install-reporting-services-sharepoint-mode"></a>安裝 Reporting Services SharePoint 模式
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在 SharePoint 中，可以在文件庫中啟用報表建立和檢視、透過電子郵件傳送報表的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱、  [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、資料警示，和報表管理功能，全部都在以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 為基礎的部署中。 如需有關 SharePoint 模式中功能的詳細資訊，請參閱 [Reporting Services 報表伺服器](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)中的＜依伺服器模式排列的功能支援與行為差異＞一節。  
  
 針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，SharePoint 模式需要安裝兩個核心 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件：  
  
|安裝|描述|  
|------------------|-----------------|  
|**報表伺服器：** 以 SharePoint 模式安裝的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器|報表伺服器處理資料與報表的處理程序、訂閱的呈現方式，以及資料警示處理程序。 SharePoint 模式報表伺服器會設計與安裝為 SharePoint 共用服務。<br /><br /> **如何：** 請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝媒體來安裝報表伺服器。|  
|**Add-in:** The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products, **rssharepoint.msi**.|增益集會在 SharePoint 網站前端伺服器上，安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用者介面 (UI) 頁面與功能。 使用者介面包含 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、SharePoint 管理中心內的管理頁面、SharePoint 文件庫中使用的功能頁面，以及 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料警示頁面。<br /><br /> **如何：**  該增益集可以從 Web 下載或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝媒體安裝。 如需詳細資訊，請參閱 [尋找適用於 SharePoint 產品之 Reporting Services 增益集的位置](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。|  
  
## <a name="in-this-section"></a>本節內容  
 [支援的 SharePoint 和 Reporting Services 伺服器與增益集的組合 &#40;SQL Server 2016&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [尋找適用於 SharePoint 產品之 Reporting Services 增益集的位置](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [在 SharePoint 模式中安裝第一部報表伺服器](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md)  
  
 [安裝或解除安裝 SharePoint 的 Reporting Services 增益集](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [將其他報表伺服器加入至伺服器陣列 &#40;SSRS 向外延展&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [將其他 Reporting Services Web 前端加入至伺服器陣列](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [設定 Reporting Services 服務應用程式的電子郵件 &#40;SharePoint 2013 和 SharePoint 2016&#41;](http://msdn.microsoft.com/en-us/38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f)  
  
 [SSRS 服務應用程式的佈建訂閱及警示](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [對 Windows Token 服務 &#40;c2WTS&#41; 和 Reporting Services 的宣告](../../reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [資料警示架構和工作流程](../../reporting-services/reporting-services-data-alerts.md#AlertingWF)   
 [警示系統管理員的資料警示管理員](../../reporting-services/data-alert-manager-for-alerting-administrators.md)  
  
  

