---
title: "設定 Power Pivot Service Accounts |Microsoft 文件"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: power-pivot-sharepoint
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76a85cd0-af93-40c9-9adf-9eb0f80b30c1
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: aae3f818de4936974dd53f14c2b3fdbbea0b369f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="configure-power-pivot-service-accounts"></a>設定 Power Pivot 服務帳戶
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]安裝包含兩個支援伺服器作業的服務。 **SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)])** 服務是一種 Windows 服務，它會在應用程式伺服器上提供 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料處理和查詢支援。 當您在 SharePoint 整合模式下安裝 Analysis Services 時，一定會在進行 SQL Server 安裝程式期間指定這個服務的登入帳戶。  
  
 此外，您必須針對 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式指定第二個帳戶，此服務應用程式是一種共用 Web 服務，其會以 SharePoint 伺服器陣列中的應用程式集區身分識別執行。 此帳戶是在使用 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]組態工具或 PowerShell 來設定 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 安裝時所指定。  
  
 每個服務都應該在專用帳戶之下執行，才能稽核連接或在伺服器陣列中啟用 Kerberos 驗證通訊協定。  
  
 一旦設定服務帳戶之後，任何一個帳戶的任何變更都必須透過 SharePoint 管理中心來完成。 如果您使用替代工具 (例如，[服務] 主控台應用程式、IIS 管理員或 SQL Server 組態管理員)，將不會為在伺服器陣列中的資料庫存取或為實體伺服器上的本機檔案存取更新權限。  
  
 本主題包含下列幾節：  
  
 [更新 SQL Server Analysis Services (Power Pivot) 執行個體的過期密碼](#bkmk_passwordssas)  
  
 [更新 Power Pivot 服務應用程式的過期密碼](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md#bkmk_passwordapp)  
  
 [變更每個服務執行所用的帳戶](#bkmk_newacct)  
  
 [建立或變更 Power Pivot 服務應用程式的應用程式集區](#bkmk_appPool)  
  
 [帳戶的需求和權限](#requirements)  
  
 [疑難排解：手動授與管理權限](#updatemanually)  
  
 [疑難排解：解決因為管理中心或 SharePoint Foundation Web 應用程式服務密碼過期而造成的 HTTP 503 錯誤](#expired)  
  
##  <a name="bkmk_passwordssas"></a> 更新 SQL Server Analysis Services (Power Pivot) 執行個體的過期密碼  
  
1.  指向 [開始]，然後按一下 **[系統管理工具]**，再按一下 **[服務]**。 按兩下 [SQL Server Analysis Services] **([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)])**。 按一下 **[登入]**，然後輸入帳戶的新密碼。  
  
2.  在 [管理中心] 的 [安全性] 區段中，按一下 **[設定 Managed 帳戶]**。  
  
3.  按一下 **[編輯]** 來變更特定的帳戶。  
  
4.  選取 **[立即變更密碼]**。  
  
5.  選取 **[將帳戶密碼設定為新的值]**。 在 Managed 帳戶下執行的所有服務都會使用更新的認證。  
  
##  <a name="bkmk_passwordapp"></a> 更新 Power Pivot 服務應用程式的過期密碼  
  
1.  在 [管理中心] 的 [安全性] 區段中，按一下 **[設定 Managed 帳戶]**。  
  
2.  按一下 **[編輯]** 來變更特定的帳戶。  
  
3.  選取 **[立即變更密碼]**。  
  
4.  選取 **[將帳戶密碼設定為新的值]**。 在 Managed 帳戶下執行的所有服務都會使用更新的認證。  
  
##  <a name="bkmk_newacct"></a> 變更每個服務執行所用的帳戶  
  
1.  在 [管理中心] 的 [安全性] 區段中，按一下 **[設定服務帳戶]**。  
  
2.  選取 **[Windows 服務 - SQL Server Analysis Services]** ，以變更 Analysis Services 服務帳戶。  
  
3.  在 **[選取此服務的帳戶]**中，選擇現有的 Managed 帳戶或建立新的 Managed 帳戶。 此帳戶必須是網域使用者帳戶。  
  
4.  選取 [服務應用程式集區 - SharePoint Web 服務系統]，以變更預設 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式的應用程式集區身分識別。 依據設定安裝的方式，服務可能會在已針對 SharePoint 服務建立的現有服務應用程式集區之中執行。 依預設，[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 組態工具會將此服務登錄為**預設的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式 ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式)**。  
  
     若此服務由 SharePoint 管理員手動設定，則此服務極可能會擁有自己的服務應用程式集區。  
  
5.  在 **[選取此服務的帳戶]**中，選擇現有的 Managed 帳戶或建立新的 Managed 帳戶。 此帳戶必須是網域使用者帳戶。  
  
6.  按一下 **[確定]**。  
  
##  <a name="bkmk_appPool"></a> 建立或變更 Power Pivot 服務應用程式的應用程式集區  
  
1.  在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]**。  
  
2.  選取 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式，但是不要在上面按一下。 按一下應用程式名稱會開啟 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理儀表板，但儀表板中並沒有通往指定應用程式集區之屬性頁面的連結。  選取 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式時，可以按一下應用程式列上的空白處，或是按一下類型名稱。  
  
3.  在功能區上按一下 **[屬性]** 。  
  
4.  選取 **[建立新的應用程式集區]**。 提供應用程式集區的名稱，並指定 Managed 帳戶做為識別。  
  
##  <a name="requirements"></a> 帳戶的需求和權限  
 在規劃 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 部署時，您必須規劃下列服務帳戶：  
  
-   Analysis Services 服務帳戶。 Analysis Services 會處理伺服器陣列中的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 查詢和資料重新整理作業。 當您安裝 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 時，在 SQL Server 安裝程式期間一律都會指定此帳戶。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式集區。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式已與 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系統服務建立關聯，後者會在伺服器陣列中提供 SharePoint 整合與 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 查詢處理的基礎結構。 您為 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式指定的應用程式集區為 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系統服務的服務識別。 您可以在伺服器陣列中具有多個 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式。 您所建立的每一個應用程式都應該在其本身的應用程式集區內執行。  
  
#### <a name="analysis-services-service-account"></a>Analysis Services 服務帳戶  
  
|需求|說明|  
|-----------------|-----------------|  
|提供需求|此帳戶必須在 SQL Server 安裝程式執行期間，使用安裝精靈中的 [Analysis Services - 組態] 頁面 (或是命令列安裝程式中的 **ASSVCACCOUNT** 安裝參數) 加以指定。<br /><br /> 您可以使用管理中心、PowerShell 或 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 組態工具，來修改使用者名稱或密碼。 不支援使用其他工具來變更帳戶和密碼。|  
|網域使用者帳戶需求|此帳戶必須是 Windows 網域使用者帳戶。 禁止使用內建電腦帳戶 (如，網路服務或本機服務)。 只要指定電腦帳戶，SQL Server 安裝程式就會封鎖安裝，以強制滿足網域使用者帳戶需求。|  
|權限需求|此帳戶必須是成員的 SQLServerMSASUser\<伺服器 > $PowerPivot 安全性群組和 WSS_WPG 安全性群組本機電腦上的。 這些權限應該會自動授與。 如需如何檢查或授與權限的詳細資訊，請參閱本主題中的 [手動授與 Power Pivot 服務帳戶管理權限](#updatemanually) 和 [初始組態 (Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)。|  
|向外延展需求|如果您在伺服器陣列中安裝多個 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 伺服器執行個體，則所有 Analysis Services 伺服器執行個體都必須在相同的網域使用者帳戶下執行。 例如，如果您設定第一個 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 執行個體，以 Contoso\ssas-srv01 的身分執行，則之後部署於相同伺服器陣列中的所有其他 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 執行個體，都必須以 Contoso\ssas-srv01 (或任何目前帳戶) 的身分執行。<br /><br /> 將所有服務執行個體設定為在相同帳戶下執行時，可讓 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系統服務將查詢處理或資料重新整理作業配置給伺服器陣列中的任何 Analysis Services 服務執行個體。 此外，也可以將管理中心的管理帳戶功能用於 Analysis Services 伺服器執行個體。 當所有 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 執行個體都使用相同的帳戶時，您可以變更帳戶或密碼一次，而所有使用這些認證的服務執行個體都會自動更新。<br /><br /> SQL Server 安裝程式會強制滿足相同帳戶需求。 在已安裝 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 執行個體之 SharePoint 伺服器陣列的向外延展部署中，如果指定的 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 帳戶與伺服器陣列中已使用的帳戶不同，則安裝程式會封鎖新的安裝。|  
  
#### <a name="power-pivot-service-application-pool"></a>Power Pivot 服務應用程式集區  
  
|需求|說明|  
|-----------------|-----------------|  
|提供需求|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系統服務是在伺服器陣列上的共用資源，並會在建立服務應用程式時提供使用。 建立服務應用程式時，必須指定服務應用程式集區。 您可透過兩種方法指定：使用 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 組態工具，或透過 PowerShell 命令。<br /><br /> 您可能已經設定應用程式集區識別在唯一帳戶下執行。 如果未指定，請考慮立即將它變更為在不同帳戶下執行。|  
|網域使用者帳戶需求|應用程式集區識別必須是 Windows 網域使用者帳戶。 禁止使用內建電腦帳戶 (如，網路服務或本機服務)。|  
|權限需求|這個帳戶不需要電腦上的本機系統管理員權限。 但是，此帳戶必須在安裝於相同電腦的本機 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 上具有 Analysis Services 系統管理員權限。 這些權限會由 SQL Server 安裝程式自動授與，或是當您在管理中心設定或變更應用程式集區識別時授與。<br /><br /> 將查詢轉送到 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]必須有系統管理權限。 在監視健全狀況、關閉非使用中的工作階段及接聽追蹤事件時也需要系統管理權限。<br /><br /> 此帳戶必須擁有 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式資料庫的連接、讀取和寫入權限。 當建立應用程式時會自動授與這些權限，當您在管理中心變更帳戶或密碼時則會自動更新這些權限。<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式將會檢查 SharePoint 使用者是否已獲得檢視資料的授權，然後再擷取檔案，但並不會模擬使用者。 模擬並不需要任何權限。|  
|向外延展需求|無。|  
  
##  <a name="updatemanually"></a> 疑難排解：手動授與管理權限  
 如果更新認證的人員不是電腦上的本機系統管理員，管理權限將無法更新。 如果發生這個情況，您可以手動授與管理權限。 最簡單的方式就是，在管理中心執行 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 組態計時器工作。 您可以使用這個方法，在伺服器陣列中重設所有 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 伺服器的權限。 請注意，此方法只有在 SharePoint 計時器工作以伺服陣列管理員或電腦本機系統管理員執行時才有作用。  
  
1.  在 [監視] 中，按一下 **[檢閱工作定義]**。  
  
2.  選取 [[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 組態計時器工作]。  
  
3.  按一下 **[立即執行]**。  
  
 最後一個步驟中，您可以確認正確權限，Analysis Services 系統管理權限授與[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]服務應用程式，並特別將服務應用程式識別加入 SQLServerMSASUser\<servername > $PowerPivot Windows 安全性群組。 您必須針對與 SharePoint 伺服陣列整合的每個 Analysis Services 執行個體重複這些步驟。  
  
 您必須是本機系統管理員才能更新 Windows 安全性群組。  
  
1.  在 SQL Server Management Studio 中，連接到 Analysis Services 執行個體\<伺服器名稱 > \POWERPIVOT。  
  
2.  以滑鼠右鍵按一下伺服器名稱，然後選取 [屬性]。  
  
3.  按一下 **[安全性]**。  
  
4.  按一下 **[加入]**。  
  
5.  輸入用於 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式集區之帳戶的名稱，然後按一下 [確定] 。  
  
6.  在 [系統管理工具] 中，按一下 **[電腦管理]**。  
  
7.  開啟 **[本機使用者和群組]**。  
  
8.  開啟 **[群組]**。  
  
9. 按兩下 SQLServerMSASUser$\<servername > $PowerPivot。  
  
10. 按一下 **[加入]**。  
  
11. 輸入用於 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式集區之帳戶的名稱，然後按一下 [確定] 。  
  
##  <a name="expired"></a> 疑難排解：解決因為管理中心或 SharePoint Foundation Web 應用程式服務密碼過期而造成的 HTTP 503 錯誤  
 如果管理中心服務或 SharePoint Foundation Web 應用程式服務因為帳戶重設或密碼過期而停止運作，當您嘗試開啟 SharePoint 管理中心或 SharePoint 網站時，將會出現 HTTP 503「服務無法使用」錯誤訊息。 請遵循這些步驟，讓您的伺服器重新回復到線上狀態。 一旦可以使用管理中心之後，您就可以繼續更新過期的帳戶資訊。  
  
1.  在 [系統管理工具] 中，按一下 **[Internet Information Services Manager]**。  
  
2.  如果網站或管理中心應用程式集區的識別是密碼過期的網域使用者帳戶，請執行下列操作：  
  
    1.  以滑鼠右鍵按一下應用程式集區名稱，然後選取 **[進階設定]**。  
  
    2.  選取 **[識別]** ，然後按一下... 按鈕，以開啟 [應用程式集區識別] 對話方塊。  
  
    3.  按一下 **[設定]**。  
  
    4.  輸入使用者名稱和密碼。  
  
3.  執行 IISRESET。 若要這樣做，開啟系統管理員命令提示字元，然後在命令處輸入 **iisreset** 。  
  
4.  在 [SharePoint 管理中心] 的 [安全性] 區段中，選取 **[設定 Managed 帳戶]**。  
  
5.  按一下 **[編輯]** 來更新密碼已過期之 Managed 帳戶的資訊。  
  
6.  選取 **[立即變更密碼]**。  
  
7.  按一下 **[使用現有的密碼]**。  
  
8.  輸入密碼，然後按一下 **[確定]**。  
  
 如果已安裝 Reporting Services，請使用 Reporting Services 組態管理員更新報表伺服器的密碼，以及報表伺服器資料庫的連接。 如需詳細資訊，請參閱[設定和管理報表伺服器 &#40;Reporting Services SharePoint 模式&#41;](../../reporting-services/report-server-sharepoint/configuration-and-administration-of-a-report-server.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [啟動或停止 Power Pivot for SharePoint Server](../../analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server.md)   
 [設定 Power Pivot 自動資料重新整理帳戶 (Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
  
