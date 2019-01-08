---
title: Analysis Services 表格式模型程式設計的相容性層級 1050年-1103年 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe2ce43ffb5d2c5be0afb39931f231d2f0d24e14
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2018
ms.locfileid: "53071765"
---
# <a name="tabular-model-programming-for-compatibility-levels-1050-through-1103"></a>相容性層級 1050 到 1103 的表格式模型程式設計
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  表格式模型使用關聯式建構，將分析和報表應用程式所使用的 Analysis Services 資料模型化。 這些模型在設定為表格式模式的 Analysis Service 執行個體上執行，對儲存體使用記憶體中分析引擎，以及在要求資料時執行彙總和計算資料的快速資料表掃描。  
  
 如果表格式模型資料庫最能符合您的自訂 BI 方案需求，您可以使用任何 Analysis Services 用戶端程式庫和程式設計介面，將您的應用程式與 Analysis Services 執行個體上的表格式模型整合。 若要查詢和計算表格式模型資料，您可以在程式碼中使用內嵌 MDX 或 DAX。  
  
 在舊版的相容性層級 1050 到 1103，特定模型的 Analysis Services 中建立的表格式模型的您以程式設計方式在 AMO、 ADOMD.NET、 XMLA 或 OLE DB 中使用的物件是基本上相同表格式和多維度方案。 具體來說，針對多維度模型定義的物件中繼資料也用於表格式模型的相容性層級 1050年-1103年。  
  
 從 SQL Server 2016 開始，表格式模型可以是內建或升級為 1200年或更高的相容性層級，來定義模型中使用表格式中繼資料。 在此層級中的中繼資料和可程式性是本質上不同。 請參閱[表格式模型程式設計相容性層級 1200 及更高版本](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)並[升級 Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)如需詳細資訊。  
  
## <a name="in-this-section"></a>本節內容  
 [商業智慧的 CSDL 註解 &#40;CSDLBI&#41;](https://docs.microsoft.com/bi-reference/csdl/csdl-annotations-for-business-intelligence-csdlbi)  
  
 [了解表格式物件模型，在相容性層級 1050年到 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [CSDL 之 BI 註解的技術參考](https://docs.microsoft.com/bi-reference/csdl/technical-reference-for-bi-annotations-to-csdl)  
  

[IMDEmbeddedData 介面](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/imdembeddeddata-interface.md)


  
  
