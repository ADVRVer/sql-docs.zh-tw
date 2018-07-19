---
title: NotificationTechnique 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- NotificationTechnique Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- NotificationTechnique element
ms.assetid: 80c43de3-f147-4bf5-bb85-da9d182ce415
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e661b47c5344b0094daef53102aada68a6b6aad9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213908"
---
# <a name="notificationtechnique-element-assl"></a>NotificationTechnique 元素 (ASSL)
  指定是否[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]或外部的用戶端應用程式會處理通知。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<ProactiveCachingBinding>  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingBinding>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|字串 (列舉)|  
|預設值|*用戶端*|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[ProactiveCachingBinding](../data-type/binding-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 這個元素的值限制為下表所列的其中一個字串。  
  
|值|描述|  
|-----------|-----------------|  
|*用戶端*|外部用戶端應用程式會處理通知。|  
|*Server*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會處理通知。|  
  
 對應至父系的元素`NotificationTechnique`在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.ProactiveCachingBinding>。  
  
 在「分析管理物件」(AMO) 物件模型中對應至 `NotificationTechnique` 允許值的列舉是 <xref:Microsoft.AnalysisServices.NotificationTechnique>。  
  
## <a name="see-also"></a>另請參閱  
 [ProactiveCachingBinding 資料類型&#40;ASSL&#41;](../data-type/binding-data-type-assl.md)  
  
  
