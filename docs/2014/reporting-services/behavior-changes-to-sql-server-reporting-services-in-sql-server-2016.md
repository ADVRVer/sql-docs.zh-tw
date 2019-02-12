---
title: SQL Server Reporting Services SQL Server 2014 中的行為變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b845480863facf66ff33c5d976531118edb2d4a9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2019
ms.locfileid: "56033189"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>SQL Server 2014 中 SQL Server Reporting Services 的行為變更
  本主題描述 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中的行為變更。 行為變更會影響 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中功能的運作或互動方式 (相較於舊版的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)])。  
  
 本主題內容：  
  
-   [SQL Server 2014 Reporting Services 行為變更](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services 行為變更](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services 行為變更](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services 行為變更  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中的 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]行為沒有任何變更。  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services 行為變更  
 本節描述 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 模式的行為變更。  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>檢視項目權限將不會下載共用資料集 (SharePoint 模式)  
 **新的行為：** 具有 「 檢視項目 」 的 SharePoint 權限的使用者無法再下載 Reporting Services 共用資料集的內容。 這項行為變更現在是一致的報表、 資料來源和模型的 「 檢視項目 」 權限。 具有 「 檢視項目 」 權限的使用者可以檢視和執行報表、 資料來源和模型，但無法下載其內容。  
  
 **先前的行為：** 擁有 SharePoint 「 檢視項目 」 權限的使用者可以下載 Reporting Services 共用資料集的內容。  
  
 如需有關 SharePoint 權限等級的詳細資訊，請參閱＜ [使用者權限與權限等級](https://technet.microsoft.com/library/cc721640.aspx)＞  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>報表伺服器追蹤記錄位於 SharePoint 模式的新位置 (SharePoint 模式)  
 **新的行為：** 對於在 SharePoint 模式下安裝的報表伺服器，報表伺服器追蹤記錄將位於 %Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles 底下。  
  
 **先前的行為：** 報表伺服器追蹤記錄類似下列路徑下找到： %Programfilesdir%\Microsoft SQL Server\\< RS_instance > services\logfiles  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>不再支援 GetServerConfigInfo SOAP API (SharePoint 模式)  
 **新的行為**:使用 PowerShell 指令程式"Get-sprsserviceapplicationservers"  
  
 **先前的行為：** 客戶可以開發 SOAP 用戶端程式碼，以與 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 端點直接進行通訊，並呼叫 GetReportServerConfigInfo()。  
  
### <a name="report-server-configuration-and-management-tools"></a>報表伺服器組態和管理工具  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>組態管理員不用於 SharePoint 模式  
 **新的行為：**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 組態管理員不再支援 SharePoint 模式的報表伺服器。 您現在可以使用 SharePoint 管理中心完成 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 模式的組態設定，因此 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 組態管理員不再支援 SharePoint 模式。 組態管理員現在僅用於原生模式的報表伺服器。  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>您無法將伺服器從一種模式變更為另一種模式  
 **新的行為：** 您無法變更伺服器模式。 如果您以原生模式安裝報表伺服器，就無法將其變更或重新設定為 SharePoint 模式。 如果您在 SharePoint 模式下安裝，可以將報表伺服器變更為原生模式。  
  
 **先前的行為：** 客戶會在 SharePoint 模式下安裝 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器。 如果客戶想要將報表伺服器切換到原生模式，可以開啟 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 組態管理員切換到原生模式，方法是，建立新的原生模式資料庫，或連線至現有的原生模式資料庫。 客戶也可以使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 組態管理員從 SharePoint 模式切換到原生模式。  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services 行為變更  
 本節描述 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中的行為變更。  
  
> [!NOTE]  
>  因為 SQL Server 2008 R2 是 SQL Server 2008 的次要版本更新，所以建議您也檢閱 SQL Server 2008 章節中的內容。  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>Reporting Services WMI 提供者程式庫中的 SecureConnectionLevel 屬性  
 中的 WMI 提供者程式庫[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]，則**SecureConnectionLevel**屬性允許的值`0`，`1`，`2`，`3`，使用`0`指出 Secure Socket Layer (SSL) 不需要任何 Web 服務方法中，`3`指出 SSL 需要所有的 Web 服務方法，並`1`和`2`指出的 Web 服務方法子集需要 SSL。 在 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中，這些值將只有兩個可能的意思：  
  
-   `0` 表示任何 Web 服務方法都不需要 SSL。  
  
-   正整數表示所有 Web 服務方法都需要 SSL。  
  
 這項變更會影響報表伺服器回應 Web 服務呼叫的方式。 例如，<xref:ReportService2005.ReportingService2005.ListSecureMethods%2A>現在不傳回任何東西如果**SecureConnectionLevel**設定為 0 中的所有方法<xref:ReportService2005.ReportingService2005>如果**SecureConnectionLevel**設為`1`， `2`，或`3`。  
  
## <a name="see-also"></a>另請參閱  
 [新功能&#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [在 SQL Server Reporting Services SQL Server 2014 中已被取代的功能](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [SQL Server Reporting Services SQL Server 2014 中已停止的功能](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [SQL Server 2014 中 SQL Server Reporting Services 的重大變更](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
