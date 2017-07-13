---
title: "安裝 Reporting 和 Internet Information Services 來並行 |Microsoft 文件"
ms.custom: 
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [Reporting Services], IIS
ms.assetid: 9b651fa5-f582-4f18-a77d-0dde95d9d211
caps.latest.revision: 40
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: f7e12ebcec8e06828430e10c377205e2421f50f4
ms.contentlocale: zh-tw
ms.lasthandoff: 07/03/2017

---

# 安裝 Reporting 和 Internet Information Services 來並行
<a id="install-reporting-and-internet-information-services-side-by-side" class="xliff"></a>

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

您可以安裝並在同一部電腦上執行 SQL Server Reporting Services (SSRS) 和網際網路資訊服務 (IIS)。 您所使用的 IIS 版本會決定必須處理的互通性問題。  
  
|IIS 版本|問題|描述|  
|-----------------|------------|-----------------|  
|8.0, 8.5|適用於某個應用程式的要求被不同的應用程式所接受。<br /><br /> HTTP.SYS 會針對 URL 保留項目強制執行優先順序規則。 如果 URL 保留項目比另一個應用程式的 URL 保留項目更弱，傳送至具有相同虛擬目錄名稱而且共同監視通訊埠 80 之應用程式的要求可能無法送達預期的目標。|在特定條件底下，在 URL 保留項目配置中取代另一個 URL 端點的已註冊端點可能會收到適用於其他應用程式的 HTTP 要求。<br /><br /> 針對報表伺服器 Web 服務和 [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] 使用唯一的虛擬目錄名稱可協助您避免這項衝突。<br /><br /> 本主題將提供有關這個狀況的詳細資訊。|  
  
## URL 保留項目的優先順序規則
<a id="precedence-rules-for-url-reservations" class="xliff"></a>  
 在您處理 IIS 與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]之間的互通性問題之前，必須了解 URL 保留項目的優先順序規則。 優先順序規則可以歸納成為下列陳述式：具有更多明確定義值的 URL 保留項目會優先接收符合此 URL 的要求。  
  
-   指定虛擬目錄的 URL 保留項目會比省略虛擬目錄的 URL 保留項目更明確。  
  
-   指定單一位址 (透過 IP 位址、完整網域名稱、網路電腦名稱或主機名稱) 的 URL 保留項目會比萬用字元更明確。  
  
-   指定強式萬用字元的 URL 保留項目會比弱式萬用字元更明確。  
  
 下列範例會顯示 URL 保留項目的範圍，從最明確到最不明確的順序排列：  
  
|範例|要求|  
|-------------|-------------|  
|`http://123.234.345.456:80/reports`|接收傳送至的所有要求`http://123.234.345.456/reports`或`http://\<computername>/reports`如果網域名稱服務可以將 IP 位址解析成該主機名稱。|  
|`http://+:80/reports`|只要此 URL 包含 "reports" 虛擬目錄名稱，便接收傳送至適用於該電腦之任何 IP 位址或主機名稱的任何要求。|  
|`http://123.234.345.456:80`|接收指定的任何要求`http://123.234.345.456`或`http://\<computername>`如果網域名稱服務可以將 IP 位址解析成該主機名稱。|  
|`http://+:80`|若為對應至 [全部指派] 的應用程式端點，便接收尚未由其他應用程式接收的要求。|  
|`http://*:80`|若為對應至 [全未指派] 的應用程式端點，便接收尚未由其他應用程式接收的要求。|  
  
 發生連接埠衝突的其中一個指標是，您將會看到下列錯誤訊息：「System.IO.FileLoadException: 由於已有另一個處理序正在使用該檔案，所以無法存取該檔案。 (來自 HRESULT 的例外狀況: 0x80070020)。」  
  
## IIS 8.0、 8.5 與 SQL Server Reporting Services URL 保留項目
<a id="url-reservations-for-iis-80-85-with-sql-server-reporting-services" class="xliff"></a>  
 根據上一節所描述的優先順序規則，您可以開始了解針對 Reporting Services 和 IIS 所定義的 URL 保留項目如何提升互通性。 Reporting Services 會接收明確指定其應用程式之虛擬目錄名稱的要求。IIS 會接收所有其餘要求，然後您可以將這些要求導向至 IIS 處理模型內部執行的應用程式。  
  
|應用程式|URL 保留項目|描述|要求接收|  
|-----------------|---------------------|-----------------|---------------------|  
|報表伺服器|`http://+:80/ReportServer`|通訊埠 80 的強式萬用字元，以及報表伺服器虛擬目錄。|在通訊埠 80 上接收指定報表伺服器虛擬目錄的所有要求。 報表伺服器 Web 服務接收的所有要求 http://\<電腦名稱 > / reportserver。|  
|入口網站|`http://+:80/Reports`|通訊埠 80 的強式萬用字元，以及 Reports 虛擬目錄。|在通訊埠 80 上接收指定 Reports 虛擬目錄的所有要求。 [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]接收所有要求 http://\<電腦名稱 > /。|  
|IIS|`http://*:80/`|通訊埠 80 的弱式萬用字元。|在通訊埠 80 上接收其他應用程式未接收的任何其餘要求。|  

## SQL Server Reporting services IIS 8.0、 8.5 上的-並存部署
<a id="side-by-side-deployments-of-sql-server-reporting-services-on-iis-80-85" class="xliff"></a>

 當 IIS 網站的虛擬目錄名稱與 Reporting Services 所使用的虛擬目錄名稱完全相同時，IIS 與 Reporting Services 之間就會發生互通性問題。 例如，假設您有下列組態：  
  
-   指派至通訊埠 80 以及名為 "Reports" 之虛擬目錄的 IIS 網站。  
  
-   報表伺服器執行個體安裝在預設組態，其中 URL 保留項目也會指定連接埠 80 和[!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]應用程式也將"Reports"用於虛擬目錄名稱。  
  
 指定這個設定，要求傳送至 http://\<電腦名稱 >: 80/reports 程式將會收到[!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]。 安裝報表伺服器執行個體之後，透過 IIS 中 Reports 虛擬目錄存取的應用程式將無法再接收要求。  
  
 如果您要執行舊版與新版 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的並存部署，可能會遇到上述路由傳送的問題。 這是因為所有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本都會使用 "ReportServer" 和 "Reports" 當做報表伺服器與 [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] 應用程式的虛擬目錄名稱，因而增加您在 IIS 中設有 "reports" 和 "reportserver" 虛擬目錄的可能性。  
  
 為了確保所有應用程式都會接收要求，請遵循下列指導方針：  
  
-   針對 Reporting Services 安裝，請使用 IIS 網站與 Reporting Services 在相同通訊埠上尚未使用的虛擬目錄名稱。 如果發生衝突，請以「僅限檔案」模式安裝 Reporting Services (使用「安裝」，但不要在安裝精靈中設定伺服器選項)，以便您可以在安裝完成之後設定虛擬目錄。 組態發生衝突的其中一個指標是，您將會看到下列錯誤訊息：System.IO.FileLoadException: 由於已有另一個處理序正在使用該檔案，所以無法存取該檔案。 (來自 HRESULT 的例外狀況: 0x80070020)。  
  
-   針對手動設定的安裝，請在設定的 URL 中採用預設命名慣例。 如果您將 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 安裝成具名執行個體，請在建立虛擬目錄時加入執行個體名稱。  

## 後續的步驟
<a id="next-steps" class="xliff"></a>

[設定報表伺服器 Url](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
[設定 URL](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
[安裝 Reporting Services 原生模式報表伺服器](../../reporting-services/install-windows/install-reporting-services-native-mode-report-server.md)  

更多問題嗎？ [請嘗試詢問 Reporting Services 論壇](http://go.microsoft.com/fwlink/?LinkId=620231)
