---
title: "Aggregation 元素 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Aggregation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Aggregation
helpviewer_keywords:
- Aggregation element
ms.assetid: f37af388-b2b3-4234-a1d6-936ee9b7f2ae
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3064c753640fb846e0965456968982e8a88aa002
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="aggregation-element-assl"></a>Aggregation 元素 (ASSL)
  定義單一彙總[分割](../../../analysis-services/scripting/objects/partition-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Aggregations>  
      <Aggregation>  
      <ID>...</ID>  
      <Name>...</Name>  
      <Dimensions>...</Dimensions>  
            <Annotations>...</Annotations>  
      <Description>...</Description>  
   </Aggregation>  
</Aggregations>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-n：出現一次以上的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[彙總](../../../analysis-services/scripting/collections/aggregations-element-assl.md)|  
|子元素|[註解](../../../analysis-services/scripting/collections/annotations-element-assl.md)，[描述](../../../analysis-services/scripting/properties/description-element-assl.md)，[維度](../../../analysis-services/scripting/collections/dimensions-element-assl.md)，[識別碼](../../../analysis-services/scripting/properties/id-element-assl.md)，[名稱](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 分析管理物件 (AMO) 物件模型中的對應元素是<xref:Microsoft.AnalysisServices.Aggregation>。  
  
## <a name="see-also"></a>另請參閱  
 [Partition 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [AggregationDesign 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)   
 [MeasureGroup 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)   
 [物件 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

