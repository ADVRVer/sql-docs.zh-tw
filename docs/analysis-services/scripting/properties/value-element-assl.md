---
title: 值元素 (ASSL) |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
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
- Value Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Value
helpviewer_keywords:
- Value element
ms.assetid: a2fad411-73fd-42df-b4e1-df2cb8454182
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8d1737040248da1ce0b391161e2de780f6098cde
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="value-element-assl"></a>Value 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  包含父元素的值。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<AlgorithmParameter> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Value>...</Value>  
   ...  
</AlgorithmParameter>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|請參閱下表。|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
|上階或父系|資料類型|  
|------------------------|---------------|  
|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|任何 simpleType|  
|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|任何 simpleType|  
|All others|字串|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)，[註解](../../../analysis-services/scripting/objects/annotation-element-assl.md)， [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)， [ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)， [ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)， [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 **值**項目包含與父物件相關聯的值。 預期值**值**元素有所不同的父項目下, 表中所述。  
  
|父元素|預期的值|  
|--------------------|--------------------|  
|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|演算法參數的值。|  
|[註解](../../../analysis-services/scripting/objects/annotation-element-assl.md)|註解的值。|  
|[Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)|用來計算關鍵效能指標 (KPI) 之值的多維度運算式 (MDX) 運算式。|  
|[ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)|報表格式參數的值。|  
|[ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)|用來計算報表參數值的 MDX 運算式。|  
|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|目前執行中執行個體之伺服器屬性的值。|  
  
 對應至父系的項目**值**在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.AlgorithmParameter>， <xref:Microsoft.AnalysisServices.Annotation>， <xref:Microsoft.AnalysisServices.Kpi>， <xref:Microsoft.AnalysisServices.ReportParameter>，和<xref:Microsoft.AnalysisServices.ServerProperty>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性 & #40;ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
