---
title: FirstDayOfWeek 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- FirstDayOfWeek Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FirstDayOfWeek
helpviewer_keywords:
- FirstDayOfWeek element
ms.assetid: d3c92fa3-b293-43b5-806e-cd1c146a3a7c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1d3901e8e7205a2fcba7ab2967cc11b37abdcf6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168200"
---
# <a name="firstdayofweek-element-assl"></a>FirstDayOfWeek 元素 (ASSL)
  定義之當週的第一天[TimeBinding](../data-type/binding-data-type-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<TimeBinding>  
   ...  
   <FirstDayOfWeek>...</FirstDayOfWeek>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|整數 (介於 1 與 7 之間，其中 1 = 星期日而 7 = 星期六)|  
|預設值|`1`|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 對應至父系的元素`FirstDayOfWeek`在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.TimeBinding>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
