---
title: FontName 元素 (ASSL) |Microsoft 文件
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
- FontName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FontName
helpviewer_keywords:
- FontName element
ms.assetid: 5560a852-9745-4abb-93d8-9cebe8a9897c
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4a58b048255bd0f079f6fc8d22d4666a3f4ced29
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36134008"
---
# <a name="fontname-element-assl"></a>FontName 元素 (ASSL)
  描述字型相關顯示特性[CalculationProperty](../objects/calculationproperty-element-assl.md)或[量值](../objects/measure-element-assl.md)父項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FontName>...</FontName>  
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
 `FontName`屬性包含多維度運算式 (MDX) 運算式，並套用至`CalculationProperty`項目具有[CalculationType](calculationtype-element-assl.md)的*成員*或*資料格*.  
  
 對應至父系的項目`FontName`在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.CalculationProperty>和<xref:Microsoft.AnalysisServices.Measure>。  
  
## <a name="see-also"></a>另請參閱  
 [CalculationProperties 元素&#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript 元素&#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts 元素&#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  