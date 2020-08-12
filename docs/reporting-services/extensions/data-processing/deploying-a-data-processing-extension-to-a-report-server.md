---
title: 如何：將資料處理延伸模組部署到報表伺服器 | Microsoft Docs
description: 了解如何將資料處理延伸模組部署到報表伺服器，方法是了解要將哪些項目新增至哪些組態檔。
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a43b94a4ef45b210ea2f54b0401962e79ca9a489
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529580"
---
# <a name="deploying-a-data-processing-extension-to-a-report-server"></a>將資料處理延伸模組部署到報表伺服器
  報表伺服器使用資料處理延伸模組來擷取和處理轉譯報表中的資料。 您應該將資料處理延伸模組組件部署到報表伺服器做為私人組件， 也需要在報表伺服器組態檔 RSReportServer.config 中建立項目。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>部署資料處理延伸模組組件  
  
1.  將組件從臨時位置複製到您要在其上使用資料處理延伸模組之報表伺服器的 bin 目錄。 報表伺服器 bin 目錄的預設位置是 %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer\bin。  
  
    > [!NOTE]  
    >  這個步驟會避免升級到 SQL Server 的新執行個體。 如需詳細資訊，請參閱＜ [Upgrade and Migrate Reporting Services](../../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)＞。  
  
2.  在複製組件檔之後，開啟 RSReportServer.config 檔。 RSReportServer.config 檔案位於 ReportServer 目錄中。 您需要在資料處理延伸模組組件檔案的組態檔中建立項目。 您可以使用 Visual Studio 或簡單的文字編輯器 (如 [記事本]) 開啟設定檔。  
  
3.  在 RSReportServer.config 檔中，找出 **Data** 元素。 應該針對您新建立的資料處理延伸模組，在下列位置建立項目：  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  針對您的資料處理延伸模組加入項目。 您的項目應該包含具有 **Name** 和 **Type** 值的 **Extension** 項目，且看起來可能如下所示：  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     **Name** 的值是資料處理延伸模組的唯一名稱。 **Type** 的值是以逗號分隔的清單，包括實作 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 和 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 介面之類別的完整命名空間項目，後面接著組件的名稱 (不包含 .dll 副檔名)。 依預設值，資料處理延伸模組是可見的。 若要在使用者介面中隱藏延伸模組 (例如報表管理員)，請將 **Visible** 屬性加入到 **Extension** 元素，並將其設定為 **false**。  
  
5.  針對為延伸模組授與 **FullTrust** 權限的自訂組件，新增程式碼群組。 這項作業的進行方式是將程式碼群組新增至 rssrvpolicy.config 檔案，此檔案預設位於 %ProgramFiles%\Microsoft SQL Server\\<MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer。 您的程式碼群組可能如下所示：  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL 成員資格僅是您可以針對資料處理延伸模組所選擇的許多成員資格條件的其中一個。 如需 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中程式碼存取安全性的詳細資訊，請參閱[安全開發 &#40;Reporting Services&#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)。  
  
## <a name="verifying-the-deployment"></a>確認部署  
 您可以使用 Web 服務 <xref:ReportService2010.ReportingService2010.ListExtensions%2A> 方法來確認資料處理延伸模組是否已成功部署到報表伺服器。 您也可以開啟報表管理員，然後確認延伸模組是否包含在可用資料來源的清單。 如需報表管理員和資料來源的詳細資訊，請參閱[建立、修改及刪除共用資料來源 &#40;SSRS&#41;](../../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)。  
  
## <a name="see-also"></a>另請參閱  
 [部署資料處理延伸模組](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Reporting Services 延伸模組](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [實作資料處理延伸模組](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 延伸模組程式庫](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
