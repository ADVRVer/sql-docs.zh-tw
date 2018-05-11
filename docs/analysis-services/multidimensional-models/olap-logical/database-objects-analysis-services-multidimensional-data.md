---
title: 資料庫物件 (Analysis Services-多維度資料) |Microsoft 文件
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 05f0dd7a7bfb6e0b32dc4838e16de3971910f2f2
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="database-objects-analysis-services---multidimensional-data"></a>資料庫物件 (Analysis Services - 多維度資料)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  A [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]執行個體包含資料庫物件和組件搭配線上分析處理 (OLAP) 和資料採礦。  
  
-   資料庫中包含 OLAP 和資料採礦物件，例如，資料來源、資料來源檢視、Cube、量值、量值群組、維度、屬性、階層、採礦結構、採礦模型及角色。  
  
-   組件中包含擴充內建函數 (由多維度運算式 (MDX) 和資料採礦延伸模組 (DMX) 語言提供) 功能的使用者自訂函數。  
  
 <xref:Microsoft.AnalysisServices.Database> 物件是商業智慧專案所需之所有資料物件 (例如 OLAP Cube、維度和資料採礦結構) 及支援物件 (例如 <xref:Microsoft.AnalysisServices.DataSource>、<xref:Microsoft.AnalysisServices.Account> 和 <xref:Microsoft.AnalysisServices.Role>) 的容器。  
  
 <xref:Microsoft.AnalysisServices.Database> 物件提供了包含以下項目之物件和屬性的存取權：  
  
-   您可以存取的所有 Cube (集合的形式)。  
  
-   您可以存取的所有維度 (集合的形式)。  
  
-   您可以存取的所有採礦結構 (集合的形式)。  
  
-   所有的資料來源和資料來源檢視 (兩個集合的形式)。  
  
-   所有的角色和資料庫權限 (兩個集合的形式)。  
  
-   資料庫的定序值。  
  
-   資料庫的預估大小。  
  
-   資料庫的語言值。  
  
-   資料庫的可見設定。  
  
## <a name="in-this-section"></a>本節內容  
 下列主題將描述在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中，OLAP 和資料採礦功能所共用的物件。  
  
|主題|Description|  
|-----------|-----------------|  
|[多維度模型中的資料來源](../../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)|描述 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中的資料來源。|  
|[多維度模型中的資料來源檢視](../../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)|描述在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中以一或多個資料來源為根據的邏輯資料模型。|  
|[多維度模型中的 cube](../../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)|描述 Cube 和 Cube 物件，包括：量值、量值群組、維度使用方式關聯性、計算、關鍵效能指標、動作、翻譯、分割與檢視方塊。|  
|[維度 &#40;Analysis Services-多維度資料 &#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|描述維度和維度物件，其中包括屬性、屬性關聯性、階層、層級與成員。|  
|[採礦結構 &#40;Analysis Services-資料採礦 &#41;](../../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)|描述採礦結構和採礦物件，其中包括採礦模型。|  
|[安全性角色 &#40;Analysis Services-多維度資料 &#41;](../../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)|描述角色，也就是在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中控制存取物件權限的安全性機制。|  
|[多維度模型組件管理](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)|描述 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中的組件，也就是用來擴充 MDX 和 DMX 語言之使用者自訂函數的集合。|  
  
## <a name="see-also"></a>另請參閱  
 [支援的資料來源 &#40;SSAS-多維度 &#41;](../../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)   
 [多維度模型方案 ](../../../analysis-services/multidimensional-models/multidimensional-model-solutions-ssas.md)   
 [資料採礦方案](../../../analysis-services/data-mining/data-mining-solutions.md)  
  
  
