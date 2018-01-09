---
title: "進度報表事件類別目錄 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- progress events [Analysis Services]
- Progress Reports event category
- event classes [Analysis Services], progress reports
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c90cfbe7e30d0678d13a329737c21f7d45575e22
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="progress-reports-event-category"></a>進度報表事件類別目錄
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]進度報表事件類別目錄具有下表中所述的事件類別。  
  
|Event Class|事件識別碼|描述|  
|-----------------|--------------|-----------------|  
|進度報表開始|5|收集自從啟動追蹤之後的所有進度報表開始事件。|  
|進度報表結束|6|收集自從啟動追蹤之後的所有進度報表結束事件。|  
|進度報表目前事件|7|收集自從啟動追蹤之後的所有進度報表目前事件。 例如，在處理期間，目前的報表會包括關於處理中物件 (維度、資料分割、Cube 等等) 的處理資訊。|  
|進度報表錯誤|8|收集自從啟動追蹤之後的所有進度報表錯誤事件。|  
  
 每一個進度報表開始事件是以進度事件資料流開始，然後以進度報表結束事件結束。 資料流可包含任何數量的進度報表目前事件和進度報表錯誤事件。  
  
 如需每個 [進度報表] 事件類別之相關資料行的資訊，請參閱 [進度報表資料行](../../analysis-services/trace-events/progress-reports-data-columns.md)。  
  
## <a name="see-also"></a>請參閱  
 [Analysis Services 追蹤事件](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
