---
title: FontSize 元素 (ASSL) |Microsoft Docs
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
- FontSize Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FontSize
helpviewer_keywords:
- FontSize element
ms.assetid: 49f66a73-946a-4fbd-9749-a3ca1b717ff3
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8f6b5ba39d52cb96061fe4d19208e6e343bab5f6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167529"
---
# <a name="fontsize-element-assl"></a>FontSize 元素 (ASSL)
  描述的字型相關顯示特性[CalculationProperty](../objects/calculationproperty-element-assl.md)或是[量值](../objects/measure-element-assl.md)父項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FontSize>...</FontSize>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[CalculationProperty](../objects/calculationproperty-element-assl.md)，[量值](../objects/measure-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 `FontSize`屬性包含多維度運算式 (MDX) 運算式，並套用至`CalculationProperty`擁有的項目[CalculationType](calculationtype-element-assl.md)的*成員*或*資料格*.  
  
 對應至父系的元素`FontSize`在 「 分析管理物件 (AMO) 物件模型所<xref:Microsoft.AnalysisServices.CalculationProperty>和<xref:Microsoft.AnalysisServices.Measure>。  
  
## <a name="see-also"></a>另請參閱  
 [CalculationProperties 元素&#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript 元素&#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts 元素&#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
