---
title: 資料採礦方案 |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4668afcd31c7eb97e398772587866636ff155459
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52543019"
---
# <a name="data-mining-solutions"></a>資料採礦方案
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  資料採礦方案是包含一個或多個資料採礦專案的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 方案。  
  
 本節的主題會提供有關如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]來設計及實作整合式資料採礦方案的資訊。 如需資料採礦設計程序與相關工具的概觀，請參閱 [資料採礦概念](../../analysis-services/data-mining/data-mining-concepts.md)。  
  
 如需有關對資料採礦非常實用之其他專案類型的詳細資訊，請參閱 [資料採礦方案的相關專案](../../analysis-services/data-mining/related-projects-for-data-mining-solutions.md)。  
  
 [關聯式與多維度方案](#bkmk_RelMD)  
  
 [部署資料採礦方案](#bkmk_Deploy)  
  
 [方案逐步解說](#bkmk_Walkthru)  
  
##  <a name="bkmk_RelMD"></a> 關聯式與多維度方案的比較  
 資料採礦方案可以是根據多維度資料-也就是現有的 cube-或單純的關聯式資料，例如資料表和資料倉儲中的檢視，或是根據文字檔、 Excel 活頁簿或其他外部資料來源。  
  
-   您可以在現有的多維度資料庫方案內建立資料採礦物件。  
  
     一般來說，如果您已經建立 Cube 而且想要使用此 Cube 當做資料來源來執行資料採礦，您就會建立這樣的方案。 當您移動和備份以 Cube 為基礎的模型時，也必須移動或複製此 Cube。  
  
-   您可以建立只包含資料採礦物件 (包括支援的資料來源和資料來源檢視) 而且只使用關聯式資料來源的資料採礦方案。  
  
     這是建立資料採礦模型的慣用方法，因為通常針對關聯式資料來源時，處理和查詢會最快速。 您也可以使用 EXPORT 和 IMPORT 命令，輕鬆地在伺服器之間移動和備份模型。  
  
##  <a name="bkmk_Deploy"></a> 部署資料採礦方案  
 部署解決方案的目標 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體必須在支援多維度物件和資料採礦物件的模式下執行；也就是說，您不能將資料採礦物件部署到裝載表格式模型或 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料的執行個體。  
  
 因此，當您在 Visual Studio 中建立資料採礦方案時，請務必使用 [Analysis Services 多維度和資料採礦專案] 範本。  
  
 當您部署方案時，用於資料採礦的物件會在指定的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體中建立 (位於與方案檔同名的資料庫中)。  
  
 如需有關如何部署關聯式和多維度方案的詳細資訊，請參閱 [部署資料採礦方案](../../analysis-services/data-mining/deployment-of-data-mining-solutions.md)。  
  
##  <a name="bkmk_Walkthru"></a> 方案逐步解說  
 提供如何使用資料採礦精靈建立資料採礦方案的概觀。  
  
 [建立關聯式採礦結構](../../analysis-services/data-mining/create-a-relational-mining-structure.md)  
 從關聯式資料、文字檔以及可以結合在資料來源檢視中的其他來源建立採礦結構。  
  
 [建立 OLAP 採礦結構](../../analysis-services/data-mining/create-an-olap-mining-structure.md)  
 建立以 OLAP Cube 中的資料為根據的採礦結構 您從 OLAP 資料建立的模型可以儲存為資料採礦維度，或者可以將此資料集和模型儲存為新的 Cube。  
  
## <a name="in-this-section"></a>本節內容  
 [資料採礦專案](../../analysis-services/data-mining/data-mining-projects.md)  
  
 [處理資料採礦物件](../../analysis-services/data-mining/processing-data-mining-objects.md)  
  
 [資料採礦方案的相關專案](../../analysis-services/data-mining/related-projects-for-data-mining-solutions.md)  
  
 [部署資料採礦方案](../../analysis-services/data-mining/deployment-of-data-mining-solutions.md)  
  
## <a name="related-tasks-and-topics"></a>相關工作和主題  
 在您建立基本的資料採礦方案 (包括資料來源和採礦結構) 之後，您可以在此方案上加入新的模型、測試和比較模型、建立預測及試驗資料子集來進行建置。  
  
 如需詳細資訊，請參閱下列連結：  
  
|工作|主題|  
|-----------|------------|  
|測試您建立的模型、驗證定型資料的品質，然後建立代表資料採礦模型精確度的圖表。|[測試及驗證 &#40;資料採礦&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)|  
|將資料填入結構和相關模型中來定型模型。 使用新的資料來更新和擴充模型。|[處理資料採礦物件](../../analysis-services/data-mining/processing-data-mining-objects.md)|  
|將篩選套用到定型資料、選擇不同的演算法或是設定進階演算法參數來自訂採礦模型。|[自訂採礦模型和結構](../../analysis-services/data-mining/customize-mining-models-and-structure.md)|  
|將篩選套用到定型模式時所使用的資料來自訂採礦模型。|[將採礦模型加入結構 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|更新和管理資料採礦方案。|Link TBD|  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦教學課程 &#40;Analysis Services&#41;](../../analysis-services/data-mining-tutorials-analysis-services.md)  
  
  
