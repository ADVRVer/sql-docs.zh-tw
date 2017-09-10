---
title: "MeasureGroupID 元素 (ASSL) |Microsoft 文件"
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
- MeasureGroupID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MeasureGroupID
helpviewer_keywords:
- MeasureGroupID element
ms.assetid: 3b075f86-dbbc-4285-8d2d-61fa722181c7
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 457ea949ced4494af926369a8e7ba60a87bbe3a9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="measuregroupid-element-assl"></a>MeasureGroupID 元素 (ASSL)
  將[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)與父元素、 繫結或超出的非正規繫結。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<ManyToManyMeasureGroupDimension> <!-- or MeasureGroupAttributeBinding, MeasureGroupBinding, PerspectiveMeasureGroup -->  
   ...  
   <MeasureGroupID>...</MeasureGroupID>  
   ...  
</ManyToManyMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串|  
|預設值|無|  
|基數|請參閱下表。|  
  
|上階或父系|基數|  
|------------------------|-----------------|  
|[ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md)|0-1：只能出現一次的選擇性元素。|  
|[MeasureGroupAttributeBinding](../../../analysis-services/scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md)， [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)和[PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md)， [MeasureGroupAttributeBinding](../../../analysis-services/scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md)， [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)， [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 對應至父系的項目**MeasureGroupID**在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.ManyToManyMeasureGroupDimension>， <xref:Microsoft.AnalysisServices.MeasureGroupBinding>，和<xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
