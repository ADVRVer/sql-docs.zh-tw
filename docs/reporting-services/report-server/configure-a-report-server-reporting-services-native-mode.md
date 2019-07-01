---
title: 設定報表伺服器 (Reporting Services 原生模式) | Microsoft Docs
ms.date: 06/18/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- report server configuration
- report servers [Reporting Services], configuring
ms.assetid: ef84ce9d-9156-48e9-8073-7e0535476932
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5723122c76b02900f6906c03efb807e58ebcc6d9
ms.sourcegitcommit: 3f2936e727cf8e63f38e5f77b33442993ee99890
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67313972"
---
# <a name="configure-a-report-server-reporting-services-native-mode"></a>設定報表伺服器 (Reporting Services 原生模式)
  根據您在安裝期間選取的選項而定，報表伺服器可能需要其他組態設定才能使用。 報表伺服器組態至少要包含以下項目：  
  
-   報表伺服器服務帳戶 (在安裝期間設定)。  
  
-   提供對報表伺服器之存取的 Web 服務 URL。  
  
-   儲存應用程式資料、報表和其他項目的報表伺服器資料庫。  
  
 如果您選取以下兩個安裝選項的其中一種，安裝程式會進行最小的設定：原生模式預設組態或 SharePoint 整合模式預設組態。 如果您在僅限檔案模式中安裝報表伺服器 (這是安裝精靈中的 **[安裝但不設定伺服器]** 選項)，則只會設定服務帳戶。 在安裝程式完成之後，必須設定 Web 服務 URL 和報表伺服器資料庫。  
  
建議您設定入口網站，以便您可以授與使用者存取報表伺服器和管理報表伺服器內容。 如果您在 SharePoint 整合模式中部署報表伺服器，請使用 SharePoint 伺服器的 Web 前端來授與存取權。  
  
 也可以視需要設定其他功能，例如報表伺服器電子郵件和自動執行帳戶。 如需詳細資訊，請參閱 [管理 Reporting Services 原生模式報表伺服器](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)。  
  
 若要設定報表伺服器，請使用 Reporting Services 組態工具。  
  
## <a name="to-minimally-configure-a-report-server-installation"></a>以最低限度的方式設定報表伺服器安裝  
  
1.  啟動 Reporting Services 組態工具，並連接到報表伺服器執行個體。 如需指示，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)。  
  
2.  按一下 **[Web 服務 URL]** ，開啟為報表伺服器設定 URL 的頁面。 如需如何定義 URL 的指示，請參閱[設定 URL &#40;SSRS 設定管理員&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)。  
  
3.  按一下 **[資料庫]** ，建立報表伺服器資料庫。 如需指示，請參閱[建立原生模式報表伺服器資料庫 &#40;SSRS 設定管理員&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)。  
  
4.  回到 **[Web 服務 URL]** 頁面，並按一下此 URL 確認它是否有效。  
  
5.  遵循「後續步驟」中的指示來完成部署。  
  
## <a name="next-steps"></a>Next Steps  
 若要完成部署，您應該設定入口網站或 SharePoint 整合。 如需詳細資訊，請參閱 < [web 入口網站設定](../../reporting-services/report-server/configure-web-portal.md)。  
  
 如果開啟了 Windows 防火牆，則設定報表伺服器使用的通訊埠很可能已關閉。 當您嘗試從遠端用戶端電腦開啟入口網站時出現空白頁面，即表示連接埠可能已關閉。 如需設定防火牆的詳細資訊，請參閱＜ [Configure a Firewall for Report Server Access](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)＞。  
  
 如果您正在使用 Windows Vista 或 Windows Server 2008，需要進行其他步驟，才能在本機開啟入口網站。 如需詳細資訊，請參閱 [設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。  
  
 建立資料夾、上傳項目及執行報表來確認您的安裝。 請依照 [驗證 Reporting Services 安裝](../../reporting-services/install-windows/verify-a-reporting-services-installation.md) 中的指示來確認安裝。  
  
## <a name="see-also"></a>另請參閱  
 [管理 Reporting Services 原生模式報表伺服器](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)   
 [Configure a Firewall for Report Server Access](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)   
 [設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)   
 [設定報表伺服器來進行遠端管理](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md)   
 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)  
  
