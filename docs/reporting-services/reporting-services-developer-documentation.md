---
title: "Reporting Services 開發人員文件 |Microsoft 文件"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
caps.latest.revision: 21
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3704373a08b29a8f36ce843db5f67a860a04a47b
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="reporting-services-developer-documentation"></a>Reporting Services 開發人員文件集
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]提供一些您可在自己的應用程式中利用的程式設計介面。 您可以使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的現有功能和能力，將自訂報表與管理工具建立到網站和 Windows 應用程式中，或是可以延伸 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 平台。  
  
 擴充 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 平台包括建立可用於資料存取、報表傳遞等的新元件與資源。 您可以將這些元件與資源行銷到在其組織中使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的公司。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 包括程式設計範例與教學課程以協助您開始。 如需詳細資訊，請參閱[Reporting Services 範例](https://msdn.microsoft.com/library/ms160954\(v=sql.110\).aspx)和[開發人員手冊： 教學課程 (Reporting Services)](https://msdn.microsoft.com/library/aa337423\(v=sql.110\).aspx)。  
  
## <a name="in-this-section"></a>섹션 내용  
 [將 Reporting Services 整合到應用程式](../reporting-services/application-integration/integrating-reporting-services-into-applications.md)  
 提供如何使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 將報表整合到自訂應用程式的概觀。 描述何時使用直接的 URL 存取，以及何時使用 Web 服務存取報表伺服器。  
  
 [報表伺服器 Web 服務](../reporting-services/report-server-web-service/report-server-web-service.md)  
 報表伺服器 Web 服務提供報表伺服器的完整功能存取。 Web 服務透過 HTTP 使用 SOAP，並設計成做為用戶端程式與報表伺服器之間的通訊介面。 Web 服務及其方法會公開報表伺服器的功能，並可讓您為任何部分的報表生命週期建立從管理到執行的自訂工具。  
  
 [URL 存取 &#40;SSRS &#41;](../reporting-services/url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 支援一組完整且以 URL 為基礎的要求，讓您得以使用快速且輕鬆的存取點來進行報表導覽和檢視。 您可以和報表伺服器 Web 服務搭配使用這項技術，將完整的報表方案整合到自訂商務應用程式。 當將報表整合為 Web 入口網站的一部分時，或是當從網頁瀏覽器檢視報表時，URL 存取將特別有用。  
  
 [Reporting Services 延伸模組](../reporting-services/extensions/reporting-services-extensions.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的模組化架構是針對擴充性所設計。 現在可以使用 Managed 程式碼 API，這樣您就可以輕鬆地開發、安裝和管理許多 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 元件取用的延伸模組。 您可以建立使用的組件[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]並加入新[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]轉譯、 安全性、 傳遞和資料處理功能，以滿足不斷成長的商務需求。  
  
 [自訂報表項目](../reporting-services/custom-report-items/custom-report-items.md)  
 描述如何建立自訂報表項目，將功能加入現有控制項的 RDL 或是擴充功能。  
  
 [將自訂組件與報表搭配使用](../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
 描述如何在報表定義中包括程式碼參考，將自訂組件與報表搭配使用。  
  
 [存取 Reporting Services WMI 提供者](../reporting-services/tools/access-the-reporting-services-wmi-provider.md)  
 描述如何使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI 提供者來管理報表伺服器部署。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services &#40;SSRS &#41;](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [報表定義語言 &#40;SSRS &#41;](../reporting-services/reports/report-definition-language-ssrs.md)   
 [技術參考 &#40;SSRS &#41;](../reporting-services/technical-reference-ssrs.md)   
 [安全開發 &#40;Reporting Services &#41;](../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
  
