---
title: "擴充 OLAP 功能 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5a502afc3be82d238dc20077c526a9f94ac47689
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="extending-olap-functionality"></a>擴充 OLAP 功能
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]身為程式設計人員，您可以透過撰寫組件、 個人化延伸模組和預存程序，以提供您想要使用移作他用在多個資料庫應用程式的功能來擴充 Analysis Services。 組件是用來將新程序和函數加入至 MDX 語言或經由個人化增益集，進而擴充多維度模型功能。  
  
 預存程序可用來呼叫外部常式，讓通用程式碼只需要開發一次並儲存在單一位置，藉以簡化 Analysis Services 資料庫的開發和實作。 預存程序可用來將 MDX 的原生功能未提供的商務功能，加入您的應用程式中。  
  
 個人化是指您加入至 Cube 以提供依照使用者變更之行為的自訂物件。 個人化並非 Cube 中的永久物件，而是用戶端應用程式在使用者工作階段期間動態套用的物件。 範例包括根據存取資料的人員變更金額的貨幣、提供個別化 KPI，或一般線上購買客戶的目標建議清單。  
  
## <a name="in-this-section"></a>本節內容  
 [透過個人化擴充 OLAP](../../../analysis-services/multidimensional-models/extending-olap/extending-olap-through-personalizations.md)  
  
 [Analysis Services 個人化延伸模組](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
 [定義預存程序](../../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
