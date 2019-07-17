---
title: 使用 「 部署精靈 」 部署模型方案 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cde312f2bfad67c6cfe61a9b8379973c1f59a56c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178519"
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a>Deploy Model Solutions Using the Deployment Wizard
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署精靈 」 會使用產生的 JSON 輸出檔[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]做為輸入檔的專案。 這些輸入檔很容易進行修改，以自訂 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案的部署。 產生的部署指令碼可以立即執行，或儲存供稍後進行部署使用。  

> [!NOTE]
> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署精靈公用程式會隨[SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) (SSMS)。 請確定您使用最新版本。 如果執行從命令提示字元中，根據預設，「 部署精靈 」 的最新版本會安裝至 C:\Program Files (x86) \Microsoft SQL Server\140\Tools\Binn\ManagementStudio。 
  
 您可以使用此處討論的精靈來進行部署， 也可以自動化部署或使用同步處理功能。 如果部署的資料庫很龐大，請考慮在目標系統上使用資料分割。 您可以使用表格式物件模型 (TOM) 」、 「 表格式模型 Scriting 語言 (TMSL) 和 「 分析管理物件 (AMO) 自動化建立分割區 」 及 「 母體擴展。  
  
> [!IMPORTANT]  
>  輸出檔或部署指令碼都不會包含使用者識別碼或密碼如果這些條件指定於在連接字串的資料來源或模擬用途。 由於在這種狀況下需要使用這些資訊進行處理，所以您將手動加入這些資訊。 如果部署不包含處理，您就可以在部署之後視需要加入此連接和模擬資訊。 如果部署包含處理，您可以在儲存之後於精靈內部或在部署指令碼中加入這項資訊。  
  
## <a name="in-this-section"></a>本節內容  
 下列主題描述如何使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈、輸入檔以及部署指令碼：  
  
|主題|描述|  
|-----------|-----------------|  
|[執行 Analysis Services 部署精靈](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)|描述可以在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈中執行的各種方式。|  
|[了解用來建立部署指令碼的輸入檔](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)|描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈使用哪些檔案做為輸入值、這些檔案中包含的內容，以及提供描述如何在這些輸入檔中修改值之主題的連結。|  
|[了解 Analysis Services 部署指令碼](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)|描述部署指令碼的內容，以及指令碼如何執行。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 XMLA 部署模型方案](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)   
 [同步處理 Analysis Services 資料庫](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [了解用來建立部署指令碼的輸入檔](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)   
 [使用部署公用程式的部署模型方案](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  
