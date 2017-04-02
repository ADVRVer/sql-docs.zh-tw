---
title: "使用精靈部署模型部署封裝 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "部署封裝 [Master Data Services], 部署"
  - "模型 [Master Data Services], 部署封裝"
ms.assetid: 4f65dc60-0ff8-46e6-9988-5bc5b9603ad0
caps.latest.revision: 16
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 16
---
# 使用精靈部署模型部署封裝
  若要部署只包含模型物件的套件，請使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 模型部署精靈。 如果您需要部署包含資料的套件，請參閱[使用 MDSModelDeploy 部署模型部署封裝](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)。  
  
> [!IMPORTANT]  
>  封裝只能部署到之前建立封裝所使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本。 這表示，在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中建立的封裝無法部署到 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]。  
  
## 必要條件  
 若要執行此程序：  
  
-   在目標 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 環境中，您必須擁有存取 [系統管理] 功能區域的權限。  
  
-   模型部署封裝必須存在。 如需詳細資訊，請參閱[使用精靈建立模型部署封裝](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)。  
  
-   您必須是您要部署模型之環境中的管理員。 如需詳細資訊，請參閱 [Administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md) (管理員 (Master Data Services))。  
  
### 若僅要部署模型物件的模型部署封裝  
  
1.  在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。  
  
2.  在 [模型檢視] 頁面上，從功能表列指向 [系統]，然後按一下 [部署]。  
  
3.  按一下 [模型部署精靈] 上的 [部署]。  
  
4.  按一下 **[瀏覽]**。  
  
5.  尋找您的部署套件 (.pkg 檔案)，然後按一下 [開啟]。  
  
6.  按一下 **[下一步]**。  
  
7.  載入套件之後，按一下 [下一步]。  
  
8.  如果模型已存在，您可以選取 [更新現有模型] 來更新模型。 若要建立新的模型，請選取 [建立新模型]，然後在按 [下一步] 之後，輸入新模型的名稱。  
  
9. 按一下 [完成] 結束精靈。  
  
 **注意：**  
  
-   如果套件中的訂閱檢視與現有模型中的訂閱檢視同名，就會顯示這項警告：**部署者訂閱已重新命名**， 且會將檢視建立為 *modelname.subscriptionviewname*。 如果此名稱已在使用中，則不會建立訂閱檢視。  
  
-   部署程序有四個步驟：  
  
    1.  建立模型物件。  
  
    2.  建立訂閱檢視。  
  
    3.  建立商務規則。  
  
-   當建立新的模型或複製的模型時，如果此程序在任何步驟期間失敗，就會刪除該模型。  
  
     更新模型時，如果此程序在前三個步驟的任何一個期間失敗，就不會繼續進行，但是，並不會回復已經進行的變更。  
  
## 後續步驟  
 檔案屬性及使用者和群組的權限不包含在模型部署封裝中。 在部署模型之後，您必須手動更新這些項目。 如需詳細資訊，請參閱：  
  
-   [指派模型物件權限 &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## 另請參閱  
 [部署模型 &#40;Master Data Services&#41;](../master-data-services/deploying-models-master-data-services.md)  
  
  