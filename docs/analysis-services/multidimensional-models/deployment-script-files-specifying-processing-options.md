---
title: "指定處理選項 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 37535b41f5ae5e7c68a47d18a4b91253c7f54d81
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="deployment-script-files---specifying-processing-options"></a>部署指令碼檔案的指定處理選項
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署精靈會讀取處理選項，從\<*專案名稱*> 部署檔案。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]建立此檔案，當您建置[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]專案。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 使用指定的處理選項**部署**頁面*\<專案名稱 >* **屬性頁**對話方塊來建立\<*專案名稱*> 部署檔案。  
  
## <a name="reviewing-the-processing-options-for-deployment"></a>檢閱部署的處理選項  
 內儲存的組態設定\<*專案名稱*> 部署檔案如下：  
  
-   **處理方法**此設定控制部署之後是否處理部署的物件，以及將要執行的處理類型。 有三個處理選項：  
  
    -   預設的處理 (預設值)  
  
    -   完整的處理  
  
    -   無  
  
-   **回寫資料表選項** 如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中已啟用回寫，則此設定會定義如何處理回寫。 有三個回寫資料表選項：  
  
    -   依預設，如果有回寫資料表，就會使用回寫資料表。 如果沒有回寫資料表，則會建立新的回寫資料表。  
  
    -   如果已經存在回寫資料表，則部署會失敗。 如果沒有回寫資料表，則會建立新的回寫資料表。  
  
    -   無論是否已存在回寫資料表，都會建立新的回寫資料表。 在此情況下，[ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈] 將刪除任何現有的資料表，並以新的回寫資料表取代。  
  
-   **交易式部署**此設定控制中繼資料變更與處理命令的部署是發生於單一交易或個別交易中。  
  
    -   如果此選項為 [True] \(預設值)，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 就會在單一交易中部署所有的中繼資料變更與所有的處理命令。  
  
    -   如果此選項為 [False]，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 就會在單一交易中部署中繼資料變更，並在個別的交易中部署每個處理命令。  
  
## <a name="modifying-the-processing-options-for-deployment"></a>修改部署的處理選項  
 不過，您可能需要部署[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]使用不同的處理選項所儲存的專案\<*專案名稱*> 部署檔案。 例如，您可能需要完整地處理所有的物件、或使用預設處理選項處理、或不進行處理。 如果 Cube 或維度是可寫入的，您可以指定使用新的或現有的回寫資料表。  
  
 若要修改部署期間使用的處理選項，您可以編輯並重建專案，或使用下列程序描述的方法之一，變更輸入檔中的處理選項。  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a>若要在已產生輸入檔之後，變更處理選項  
  
-   以互動方式執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈。 在 [處理選項] 頁面上，指定正在部署之專案的處理選項。  
  
     – 或 –  
  
-   在命令提示字元下執行 [ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈]，並將精靈設定為以回應檔案模式執行。 如需回應檔案模式的詳細資訊，請參閱 [執行 Analysis Services 部署精靈](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)。  
  
     – 或 –  
  
-   修改\<*專案名稱*> 部署檔案，使用任何文字編輯器。  
  
## <a name="see-also"></a>另請參閱  
 [指定安裝目標](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [指定資料分割和角色部署選項](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [指定方案部署的組態設定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
