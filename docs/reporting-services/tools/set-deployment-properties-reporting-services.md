---
title: 設定部署屬性 (Reporting Services) | Microsoft Docs
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], deploying
- publishing reports [Reporting Services]
- properties [Reporting Services], deployment
- deploying reports [Reporting Services]
ms.assetid: 18201ca0-bf4a-484f-b3a2-95d1046a6a9b
author: maggiesMSFT
ms.author: maggies
ms.date: 05/15/2019
ms.openlocfilehash: 9106c4c45845d1e31d65180c8f0fd979e7e3e14c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "66175335"
---
# <a name="set-deployment-properties-reporting-services"></a>設定部署屬性 (Reporting Services)

  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或 Visual Studio 中，您必須為報表及共用資料來源指定報表伺服器和資料夾 (選擇性)，讓您可以將報表伺服器專案中的項目發行至報表伺服器。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或 Visual Studio 建置、預覽及部署報表所需的屬性和值都儲存在報表伺服器專案的專案組態中。 您可以為這些專案屬性建立多個命名集，讓您可以在屬性集之間方便地切換。 每一組屬性都是一個組態。 例如，您可以擁有一個組態將報表發行到測試伺服器，並有另一個組態將報表發行到實際伺服器。  
  
 使用組態管理員可在專案組態中建立及管理專案屬性的集合。 組態管理員是 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]支援的功能， [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 是以它為基礎。  
  
> [!NOTE]  
> 請不要將這項功能與 Reporting Services 組態管理員搞混，後者是用來在安裝之後設定 Reporting Services。 如需詳細資訊，請參閱[設定和管理報表伺服器 &#40;SSRS 原生模式&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)。  
>
> [!NOTE]  
> 在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中，從報表伺服器專案或解決方案發行報表的動作稱為「部署報表」  。  
  
## <a name="to-set-deployment-properties"></a>若要設定部署屬性
  
1. 以滑鼠右鍵按一下報表專案，然後按一下 [屬性]  。  
  
2. 在專案的 [屬性頁面]  對話方塊中，從 [組態]  清單中選取要編輯的組態。 常見的組態為 **DebugLocal**、**Debug** 和 **Release**。  
  
    > [!NOTE]  
    > 您可以使用多個組態，在不同的報表伺服器或設定之間快速切換。  
  
3. 在 [OutputPath]  文字方塊中，鍵入或貼入本機檔案系統中的路徑，以儲存用於報表組建驗證、部署及預覽的報表定義。 此路徑必須不同於專案所使用的路徑以及位於專案路徑下之子資料夾的相對路徑。  
  
4. 在 [ErrorLevel]  文字方塊中，鍵入回報為錯誤之組建問題的嚴重性。 建置嚴重性層級小於或等於 [ErrorLevel]  值之報表、資料來源或其他專案資源時，所發生的問題會回報為錯誤；否則，系統會將這些問題回報為警告。 任何錯誤都會導致建立工作失敗。 有效的嚴重性層級為 0 到 4 (包含)。 預設值為 2。  
  
     [ErrorLevel]  可用來增加或減少組建的敏感度。 例如，在部署到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 報表伺服器期間建立包含對應的報表時，預設會顯示一個錯誤，而且報表的建立會失敗。 如果您降低 [ErrorLevel]  ，就會從報表移除對應、顯示警告，並繼續建置報表。  
  
5. 在 [StartItem]  清單中，選取執行報表專案時，要顯示在預覽視窗或瀏覽器視窗中的報表。  
  
6. 在 [OverwriteDataSources]  清單中，選取 [True]  即可在每次發行共用資料來源時覆寫伺服器上的共用資料來源，或選取 [False]  則可保留伺服器上的資料來源。  
  
7. 在 [TargetServerVersion]  清單中，選取 SQL Server 2016 版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，或選取 [偵測版本]  以自動判斷安裝在 **TargetServer URL** 屬性所識別之伺服器上的版本。 預設值為 **SQL Server 2016 或更新版本**。  
  
     使用 **TargetServerVersion** 針對 **TargetServer URL** 中指定的報表伺服器版本自訂已建置的報表 (放在 OutputPath 中指定的路徑)。  
  
8. 在 [TargetDataSourceFolder]  文字方塊中，鍵入報表伺服器上的資料夾，以放入已發行的共用資料來源。 [TargetDataSourceFolder]  的預設值為 Data Sources。 如果這個值保留空白，資料來源就會發行至 [TargetReportFolder]  中所指定的位置。  
  
9. 在 [TargetReportFolder]  文字方塊中，鍵入報表伺服器上的資料夾，以放入已發行的報表。 [TargetReportFolder]  的預設值為報表專案的名稱。  
  
    > [!NOTE]  
    > 如果是以原生模式執行的報表伺服器，您必須具有目標資料夾的「發行」  權限，才能將報表發行至該資料夾。 「發行」權限是透過將您的使用者帳戶對應到包含發行作業之角色的角色指派來提供。 如需詳細資訊，請參閱 [建立和管理角色指派](../../reporting-services/security/create-and-manage-role-assignments.md)。 如果是以 SharePoint 整合模式執行的報表伺服器，您必須具有 SharePoint 網站的「成員」  或「擁有者」  權限。 如需詳細資訊，請參閱 [報表伺服器項目的 SharePoint 網站和清單權限參考](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)。  
  
10. 在 [TargetServerURL]  文字方塊中，鍵入目標報表伺服器的 URL。 在發行報表之前，您必須設定此屬性為有效的報表伺服器 URL。 當您發行至以原生模式執行的報表伺服器時，請使用報表伺服器之虛擬目錄的 URL (例如 http: *//server/reportserver* 或 https: *//server/reportserver*)。 這是報表伺服器的虛擬目錄，而非 Web 入口網站。  
  
     發行至以 SharePoint 整合模式執行的報表伺服器時，請使用 SharePoint 頂層網站或子網站的 URL。 若未指定網站，則使用預設的最上層網站 (例如，<https://*servername*>、<https://*servername*/*site*> 或 <https://*servername*/*site*/*subsite*>)。  
  
## <a name="to-set-configuration-manager-properties"></a>設定組態管理員屬性  
  
1. 以滑鼠右鍵按一下報表專案，然後按一下 [屬性]  。  
  
2. 在專案的 [屬性頁面]  對話方塊中，按一下 [組態管理員]  。  
  
3. 在 [組態管理員]  對話方塊中，選取要編輯的組態。 目前使用中的組態會顯示為**使用中(***\<組態>***)** 。  
  
4. 在 [專案內容]  中，針對方案中的每個專案，選取或清除 [建立]  或 [部署]  。  
  
    > [!NOTE]  
    > 如果選取 [建置]  ，則報表設計師會建置報表專案，並在預覽或發行至報表伺服器之前，先檢查是否有錯誤。 如果選取 [部署]  ，則報表設計師會依照部署屬性中的定義，將報表發行至報表伺服器。 如果未選取 [部署]  ，報表設計師會在本機預覽視窗內，顯示 **StartItem** 屬性中指定的報表。  
  
## <a name="see-also"></a>另請參閱  

- [發行資料來源與報表](../../reporting-services/reports/publishing-data-sources-and-reports.md)
- [預覽報表](../../reporting-services/reports/previewing-reports.md)
- [報表設計師 F1 說明](../../reporting-services/tools/report-designer-f1-help.md)
- [SharePoint 模式在報表伺服器上已發行報表項目的 URL 範例 &#40;SSRS&#41;](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)
- [專案屬性頁對話方塊](../../reporting-services/tools/project-property-pages-dialog-box.md)
- [將報表發行至報表伺服器](../../reporting-services/reports/publishing-reports-to-a-report-server.md)
