---
title: 報表伺服器狀態（SSRS 原生模式） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.serverstatus.F1
ms.assetid: 2f63ad1c-1bc2-449d-b451-fb39a0060838
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 15a177080792eb26273399f41aad577962885376
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952463"
---
# <a name="report-server-status-ssrs-native-mode"></a>報表伺服器狀態 (SSRS 原生模式)
  使用此頁面可檢視目前所連接之報表伺服器執行個體的相關資訊。 此頁面是報表伺服器組態的起始頁面。 其他頁面可用於設定 URL、服務帳戶、報表伺服器資料庫、報表伺服器電子郵件傳遞、向外延展部署和加密金鑰。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。  
  
 若要開啟此頁面，請啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員，並連接到報表伺服器執行個體。 如需詳細資訊，請參閱[Reporting Services 組態管理員 &#40;del&#41;](reporting-services-configuration-manager-native-mode.md)。  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager （rsconfigtool.exe）是以 "highestAvailable" 的許可權層級來安裝。 這是設計的行為。 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員需要與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API 進行通訊。 某些 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 通訊需要更高層級或系統管理權限。  
  
 如果您連接至報表伺服器，而且所有頁面連結都呈現灰色，請確認報表伺服器服務是否已啟動。 **報表服務狀態：** 應該是「已啟動」。 您也可以使用 [系統管理工具] 中的 [服務] 主控台應用程式來檢查服務狀態。  
  
## <a name="options"></a>選項。  
 **SQL Server 執行個體**  
 顯示目前所連接報表伺服器執行個體的相關資訊。 報表伺服器執行個體名稱是以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 具名執行個體為基礎。 預設執行個體為 MSSQLSERVER。 具名執行個體將會是您在安裝期間所指定的值。 如需實例的詳細資訊，請參閱《線上叢書》中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的使用[多個版本和 SQL Server 的實例](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)。  
  
> [!NOTE]  
>  在 SQL Server Express with Advanced Services 中，預設執行個體為 SQLExpress。  
  
 **執行個體識別碼**  
 對應至檔案系統上儲存您所連接之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的程式檔案的資料夾。 
  **[執行個體識別碼]** 值是由安裝程式使用 *&lt;component&gt;*.*&lt;instance&gt;* 格式指派的，其中 *&lt;component&gt;* 是表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件的值，而 *&lt;instance&gt;* 是執行個體名稱。 預設執行個體名稱是 MSSQLSERVER。 例如，如果您安裝 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件的預設執行個體，對應的資料夾名稱如下：  
  
-   MSSQL12.MSSQLSERVER  
  
-   MSAS12.MSSQLSERVER  
  
-   MSRS12.MSSQLSERVER  
  
 如果您安裝已安裝之元件的第二個實例（例如[!INCLUDE[ssDE](../../includes/ssde-md.md)]），而且您將實例命名為 Contoso，則**實例識別碼**會是 mssql12.contoso。Contoso.  
  
 **公告**  
 顯示版本資訊。 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本支援的功能清單，請參閱 [SQL Server 版本支援的功能](https://go.microsoft.com/fwlink/?linkid=232473)。  
  
 **產品版本**  
 顯示您安裝的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本。  
  
 **報表伺服器資料庫**  
 顯示可儲存目前報表伺服器執行個體之應用程式資料的報表伺服器資料庫名稱。  
  
 **報表伺服器模式**  
 這裡顯示的值應該一律為 **[原生]**。 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員僅支援原生模式報表伺服器。 如果您看見 **SharePoint 整合模式**這個值，可能表示您的原生模式部署未正確設定，而且您需要連接到原生模式報表目錄。 使用組態管理員的 **[資料庫]** 頁面可變更資料庫，以及建立新的資料庫或連接到現有的原生模式報表伺服器資料庫目錄。  
  
 **伺服器狀態**  
 顯示報表伺服器服務是否在執行。  
  
 **Start**  
 啟動報表伺服器服務。 在某些組態變更之後，就必須重新啟動此服務 (例如，在變更電腦名稱之後重新設定報表伺服器時)。 如果您重新設定 URL 保留項目，此服務將會自動重新啟動。 在挑選變更時，需要重新啟動。  
  
 **停止**  
 停止報表伺服器服務。 停止此服務會造成報表伺服器停止運作。 如需詳細資訊，請參閱《線上叢書》中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [的啟動和停止報表伺服器服務](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 組態管理員 &#40;SSRS 原生模式的 F1 說明主題&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Reporting Services 組態管理員 &#40;del&#41;](/sql/sql-server/install/reporting-services-configuration-manager-native-mode)   
 [初始化報表伺服器 &#40;SSRS 組態管理員&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
