---
title: Visible 元素 (ASSL) |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Visible Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Visible
helpviewer_keywords:
- Visible element
ms.assetid: 3e9baf1b-351f-4ebf-b57d-13d561f72d6f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d47e6f1d64fb1868fc0e06cb9f806c49e17d3ba8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="visible-element-assl"></a>Visible 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  決定父元素的可見性。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CalculationProperty> <!-- or one of the elements listed below in the Element Relationships table -->  
  
   <Visible >...</Visible >  
  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|布林|  
|預設值|True|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)， [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)， [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)， [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)，[資料庫](../../../analysis-services/scripting/objects/database-element-assl.md)，[量值](../../../analysis-services/scripting/objects/measure-element-assl.md)， [MemberProperty](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 **看得見**元素會決定使用者介面元件是否應該顯示父項目。  
  
 對應至父系的項目**看得見**在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.CalculationProperty>， <xref:Microsoft.AnalysisServices.Cube>， <xref:Microsoft.AnalysisServices.CubeDimension>， <xref:Microsoft.AnalysisServices.CubeHierarchy>， <xref:Microsoft.AnalysisServices.Database>，和<xref:Microsoft.AnalysisServices.Measure>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性 & #40;ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
