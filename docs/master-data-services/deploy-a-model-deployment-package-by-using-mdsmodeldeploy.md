---
title: 部署模型部署套件（MDSModelDeploy）
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: fb2a4df4-5e0d-4b34-818f-383dbde1b15c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3ae40a50eb9866b452efb8d387df62f8bed8fa24
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728304"
---
# <a name="deploy-a-model-deployment-package-by-using-mdsmodeldeploy"></a>使用 MDSModelDeploy 部署模型部署封裝

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，使用 MDSModelDeploy 工具來部署封裝，其中包含下列其中一項：  
  
-   僅限模型物件。  
  
-   模型物件和資料。  
  
 如果您想要部署只包含模型物件的封裝，您可以在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中改用模型部署精靈。 如需詳細資訊，請參閱 [使用精靈部署模型部署封裝](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)。  
  
> [!IMPORTANT]  
>  封裝只能部署到之前建立封裝所使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本。 這表示，在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中建立的套件無法部署到 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 或更高版本。  
  
## <a name="prerequisites"></a>Prerequisites  
 若要執行此程序：  
  
-   在目標 ** 環境中，您必須擁有存取 [系統管理]**[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 功能區域的權限。  
  
-   模型部署封裝必須存在。 如需詳細資訊，請參閱  [使用 MDSModelDeploy 建立模型部署套件](../master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)。  
  
-   您必須是您要部署模型之環境中的管理員。 如需詳細資訊，請參閱 [管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)，您就可以在群組中加入及移除使用者。  
  
-   如果您正在使用資料更新模型，您所部署的目標版本不得為 [已鎖定]**** 或 [已認可]****。  
  
### <a name="to-deploy-a-model-deployment-package"></a>若要部署模型部署封裝  
  
1.  決定您要部署新的模型、模型的複製，還是更新之前複製的模型。 如需詳細資訊，請參閱[模型部署選項 &#40;Master Data Services&#41;](../master-data-services/model-deployment-options-master-data-services.md)。  
  
2.  開啟系統管理員：命令提示字元，並導覽至 MDSModelDeploy.exe。  
  
    -   如果 MDS 已安裝在預設位置，此工具會在 *drive*:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration 中。  
  
    -   如果 MDS 未安裝在預設位置，請搜尋本機電腦中的 MDSModelDeploy.exe。  
  
3.  選擇性。 檢視選項和說明。  
  
    -   若要顯示所有可用的選項，請輸入 `MDSModelDeploy` ，然後按 Enter 鍵。  
  
    -   若要顯示某個選項的説明，請輸入 *，其中* OptionName `MDSModelDeploy help OptionName`是選項的名稱。  
  
4.  選擇性。 如果您有多個 Web 應用程式，請輸入以下命令並按 Enter 鍵，以判斷您要部署的目標服務名稱：  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     隨即傳回值的清單，例如 `MDS1, Default Web Site, MDS`。 此清單中的第一個值 (此案例中為 `MDS1`) 是部署模型所需的項目。  
  
5.  根據您是建立模型、複製模型還是更新模型，在命令提示字元輸入以下命令並按 Enter 鍵。  
  
    -   若要建立新模型：  
  
        ```  
        MDSModelDeploy deploynew -package PackageName -model ModelName -service ServiceName  
        ```  
  
    -   若要建立模型的複製：  
  
        ```  
        MDSModelDeploy deployclone -package PackageName  
        ```  
  
    -   若要更新現有的模型及其資料：  
  
        ```  
        MDSModelDeploy deployupdate -package PackageName -version VersionName  
        ```  
  
    > [!IMPORTANT]  
    >  如果您使用 MDSModelDeploy 工具來更新現有模型及其資料，而且封裝不包含存在目的地模型中的實體、屬性或成員，MDSModelDeploy 就不會從模型中刪除該實體、屬性或成員。  
  
     其中 *PackageName* 是套件 (.pkg) 檔案的名稱、 *ModelName* 是新模型的名稱、 *VersionName* 是版本的名稱，而 *ServiceName* 是您在上一個步驟傳回的服務名稱。 確定模型和版本名稱符合區分大小寫的精確名稱。  
  
6.  當成功部署套件後，隨即顯示一則訊息，表示「MDSModelDeploy 作業已順利完成」。  
  
 **紀錄**  
  
-   如果套件中的訂閱檢視與現有模型中的訂閱檢視同名，就會顯示這項警告： **部署者訂閱檢視已重新命名** ，且會將檢視建立為 *modelname.subscriptionviewname*。 如果此名稱已在使用中，則不會建立訂閱檢視。  
  
-   部署程序有四個步驟：  
  
    1.  建立模型物件。  
  
    2.  建立商務規則。  
  
    3.  建立訂閱檢視。  
  
    4.  擴展主要資料。  
  
-   當建立新的模型或複製的模型時，如果此程序在任何步驟期間失敗，就會刪除該模型。  
  
     更新模型時，如果此程序在前三個步驟期間失敗，就不會繼續進行，但是，並不會回復已經進行的變更。 如果此程序在步驟 4 失敗，則會更新可以更新的成員。  
  
## <a name="next-steps"></a>後續步驟  
 檔案屬性及使用者和群組的權限不包含在模型部署封裝中。 在部署模型之後，您必須手動更新這些項目。 如需詳細資訊，請參閱  
  
-   [指派模型物件使用權限 &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Master Data Services 部署模型&#41;](../master-data-services/deploying-models-master-data-services.md)  
  
  
