---
title: CalculationProperties 元素 (ASSL) |Microsoft 文件
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- CalculationProperties Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CalculationProperties
helpviewer_keywords:
- CalculationProperties element
ms.assetid: dccfe036-0b1b-4877-8bdd-4b128ccb55c9
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 22115f16242c685b1c32f7e15fb71849e55e8043
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="calculationproperties-element-assl"></a>CalculationProperties 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  包含集合[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)與相關聯的項目[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<MdxScript>  
   ...  
   <CalculationProperties>  
      <CalculationProperty>...</CalculationProperty>  
   </CalculationProperties>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)|  
|子元素|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 分析管理物件 (AMO) 物件模型中的對應元素是<xref:Microsoft.AnalysisServices.CalculationPropertyCollection>。  
  
## <a name="see-also"></a>另請參閱  
 [集合 & #40;ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
