---
title: Reporting Services 工具 | Microsoft Docs
description: 了解 SQL Server Reporting Services 包含的部署、組態、管理與報表檢視工具。
ms.date: 06/06/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
helpviewer_keywords:
- SSRS, tools
- Reporting Services, tools
- components [Reporting Services]
- components [Reporting Services], about components
- Reporting Services, components
- SSRS, components
- reports [Reporting Services], tools
- SQL Server Reporting Services, components
- SQL Server Reporting Services, tools
- architecture [Reporting Services]
ms.assetid: 23d616e3-eb90-43fb-9b7a-869bd7e22e7b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b19b5aed9dcd3f40bb603606eeb0ae4df43beb0b
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91892298"
---
# <a name="reporting-services-tools"></a>Reporting Services 工具
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 包含一組圖形和指令碼工具，支援在受控環境中開發與使用豐富的報表功能。 此工具集包含開發工具、組態與管理工具，以及報表檢視工具。 本文提供 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中各個工具與其存取方式的簡短概觀。  
  
 如需立即找到工具，請參閱[教學課程：如何尋找及啟動 Reporting Services 工具 &#40;SSRS&#41;](../../reporting-services/tools/tutorial-how-to-locate-and-start-reporting-services-tools-ssrs.md)。  
  
## <a name="tools-for-report-authoring"></a>適用於報表撰寫的工具  
 下表列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中可用於報表撰寫的工具。  
  
|工具|說明|如何存取|  
|----------|-----------------|-------------------|  
|[!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]|使用 [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)]，您可以建立行動報表，動態調整內容以放入您的螢幕或瀏覽器視窗，並適當地縮放成任何螢幕大小。<br /><br /> 您可以在可調整格線列和欄，並具有彈性的行動報表元素的設計介面上，建立行動報表。<br /><br /> 如需詳細資訊，請參閱 [使用 SQL Server 行動報表發行工具建立行動報表](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)。|下載 [SQL Server 行動報表發行工具](https://go.microsoft.com/fwlink/?LinkId=733527)|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]|互動式的資料探索和視覺呈現體驗設計為可讓您建立以及與依據 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表格式模型的報表進行互動。|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在 SharePoint 模式中。 Sliverlight 瀏覽器|  
|報表設計師|使用此工具設計報表。 包括下列功能：<br /><br /> 部署至原生模式或 SharePoint 模式報表伺服器。<br /><br /> 裝載於 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<br /><br /> 報表資料窗格可組織用於報表的資料<br /><br /> 互動式報表設計之 [設計] 和 [預覽] 的索引標籤式檢視<br /><br /> 查詢設計工具可協助您指定要從資料來源擷取的資料，且此資料來源與 [RSReportDesigner 組態檔](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)中資料來源類型相關聯。<br /><br /> 使用智慧感知的運算式編輯器可建立自訂報表內容和外觀的 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 運算式<br /><br /> 支援自訂報表項目和自訂查詢設計工具<br /><br /> <br /><br /> 如需詳細資訊，請參閱 [SQL Server Data Tools &#40;SSDT&#41; 中的 Reporting Services](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)。|[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|  
|報表產生器|使用此工具設計報表。 包括下列功能：<br /><br /> 部署至原生模式或 SharePoint 模式報表伺服器。<br /><br /> [!INCLUDE[msCoName](../../includes/msconame-md.md)] 與 Office 相似的製作環境[!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]<br /><br /> 將報表項目儲存為報表組件的能力<br /><br /> 建立地圖精靈<br /><br /> 彙總的彙總<br /><br /> 增強的運算式支援<br /><br /> 查詢設計工具可協助您指定要從內建資料來源類型擷取的資料<br /><br /> 如需詳細資訊，請參閱 [SQL Server 的報表產生器](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)。|下載 [單機版報表產生器](https://go.microsoft.com/fwlink/?LinkID=219138)<br /><br /> 或從入口網站/SharePoint 開啟|  
  
## <a name="tools-for-report-server-administration"></a>適用於報表伺服器管理的工具  
 一組圖形和指令碼工具可用於管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的報表伺服器。 所使用工具取決於報表伺服器的部署模式。  
  
### <a name="native-mode"></a>原生模式  
 下表列出可用以管理部署於原生模式中報表伺服器的工具。  
  
|工具|說明|如何存取|  
|----------|-----------------|-------------------|  
|報表伺服器組態管理員|請使用此工具設定 Reporting Services 安裝。 可用的工作包括：<br /><br />  設定報表伺服器服務帳戶。<br /><br /> 建立及設定一個或多個 Web 服務 URL。<br /><br /> 設定入口網站 URL<br /><br /> 建立及設定報表伺服器資料庫。<br /><br /> 設定向外延展部署。<br /><br /> 備份、還原或取代用於加密已儲存之連接字串和認證的對稱金鑰。<br /><br /> 設定自動執行帳戶。<br /><br /> 設定訂閱設定。<br /><br /> 設定電子郵件傳遞的 SMTP 伺服器。<br /><br /> 設定 Power BI 服務 (雲端)。<br /><br /> 注意：報表伺服器組態管理員無助於管理報表伺服器內容、啟用其他功能，或授與伺服器存取權。<br /><br /> 如需詳細資訊，請參閱[報表伺服器組態管理員 &#40;原生模式&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)。|開始功能表|  
|SQL Server Management Studio|使用此工具即可在單一環境中管理一個或多個報表伺服器執行個體，包括：<br /><br /> 管理本機和遠端報表伺服器執行個體<br /><br /> 設定報表伺服器屬性<br /><br /> 修改角色定義<br /><br /> 關閉您不要使用的報表伺服器功能<br /><br /> 管理作業<br /><br /> 管理共用排程|開始功能表|   
|Rsconfig 公用程式|使用此工具可設定及管理連線到報表伺服器資料庫的報表伺服器。 您也可以使用它來指定自動執行報表處理所使用的使用者帳戶。<br /><br /> 如需詳細資訊，請參閱[報表伺服器命令提示字元公用程式 &#40;SSRS&#41;](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md)。|命令提示字元|  
|Rskeymgmt 公用程式|使用此工具可以：<br /><br /> 擷取、還原、建立及刪除用於加密報表伺服器資料的對稱金鑰<br /><br /> 在向外延展部署中加入報表伺服器執行個體<br /><br /> <br /><br /> 如需詳細資訊，請參閱[報表伺服器命令提示字元公用程式 &#40;SSRS&#41;](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md)。|命令提示字元|  
|Windows Management Instrumentation (WMI) 類別|使用這些類別可自動化報表伺服器組態管理員中的組態工作，且無須使用圖形化使用者介面。<br /><br /> 如需詳細資訊，請參閱 [以程式設計方式存取 WMI 提供者](../../reporting-services/accessing-the-wmi-provider-programmatically.md)。|Visual Basic 指令碼|  
  
### <a name="sharepoint-integrated-mode"></a>SharePoint 整合模式  
 在 SharePoint 模式中，Reporting Services 是在 SharePoint 架構中的服務應用程式，並且直接透過 SharePoint 進行管理  
  
|工具|說明|如何存取|  
|----------|-----------------|-------------------|  
|SharePoint 管理中心|使用 SharePoint 管理中心可建立、查詢及管理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的共用服務應用程式。<br /><br /> 如需詳細資訊，請參閱[設定和管理報表伺服器 &#40;Reporting Services SharePoint 模式&#41;](../../reporting-services/report-server-sharepoint/configuration-and-administration-of-a-report-server.md)。|前往管理中心之 SharePoint 網站 URL 的瀏覽器|  
|PowerShell Cmdlet|使用 PowerShell Cmdlet 可建立、查詢及管理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的共用服務應用程式。<br /><br /> 如需詳細資訊，請參閱 [Reporting Services SharePoint 模式的 PowerShell Cmdlet](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)。|SharePoint 2010 管理命令介面|  
  
## <a name="tools-for-report-content-management"></a>適用於報表內容管理的工具  
 一組圖形和指令碼工具可用於管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的內容。 所使用工具取決於報表伺服器的部署模式。  
  
|工具|說明|如何存取|  
|----------|-----------------|-------------------|  
|報表伺服器 Web 服務 URL|使用此工具可在一般項目瀏覽頁面的報表目錄中瀏覽內容。<br /><br /> 如需詳細資訊，請參閱 [Report Server Web Service](../../reporting-services/report-server-web-service/report-server-web-service.md)。|瀏覽器|  
|入口網站|**(僅限於原生模式)** 使用此工具可從遠端位置透過 HTTP 連線管理單一報表伺服器執行個體。 您可以執行下列工作：<br /><br /> 檢視、搜尋、列印與訂閱報表。<br /><br /> 建立、保護和維護資料夾階層，以組織伺服器上的項目。<br /><br /> 設定以角色為基礎的安全性，此安全性決定對項目與作業的存取權。<br /><br /> 設定報表執行屬性、報表記錄和報表參數。<br /><br /> 建立可連接並可從 Microsoft SQL Server Analysis Services 資料來源或從 SQL Server 關聯式資料來源擷取資料的報表模型。<br /><br /> 設定模型項目安全性以存取模型中的特定項目，或將項目對應到您事先建立之預先定義的點選連結報表。<br /><br /> 建立共用排程與共用資料來源，讓排程與資料來源連接更容易管理。<br /><br /> 建立資料驅動訂閱，將報表傳遞至大型收件者清單。<br /><br /> 建立連結報表，以重複使用並以不同的方式重新決定現有報表的用途。<br /><br /> 啟動報表產生器來建立可以在報表伺服器上儲存與執行的報表。 如需詳細資訊，請參閱[報表伺服器的入口網站 (SSRS 原生模式)](../../reporting-services/web-portal-ssrs-native-mode.md)。| 瀏覽器  
|RS 公用程式|此工具是您可用於執行編寫指令碼作業的 Script Host。 使用此工具即可執行 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 指令碼，於報表伺服器資料庫間複製資料、發行報表、在報表伺服器資料庫中建立項目等等。 如需詳細資訊，請參閱[報表伺服器命令提示字元公用程式 &#40;SSRS&#41;](../../reporting-services/tools/report-server-command-prompt-utilities-ssrs.md)。|命令提示字元|  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services Report Server](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)   
 [Reporting Services 概念 &#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [什麼是 SQL Server Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  