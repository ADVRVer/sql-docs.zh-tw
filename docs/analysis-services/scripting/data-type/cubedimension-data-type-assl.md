---
title: "CubeDimension 資料類型 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: CubeDimension Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CubeDimension
helpviewer_keywords: CubeDimension data type
ms.assetid: 128ac790-65a1-4e35-b909-8dba2a61b24c
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 63ce4755b2cf28ec2805b8e0eb32121b399816ab
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="cubedimension-data-type-assl"></a>CubeDimension 資料類型 (ASSL)
  定義代表維度與 Cube 之間關聯性的基本資料類型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CubeDimension>  
      <ID>...</ID>  
   <Name>...</Name>  
   <Translations>...</Translations>  
   <DimensionID>...</DimensionID>  
   <Visible>...</Visible>  
   <AllMemberAggregationUsage>...</AllMemberAggregationUsage>  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
      <Attributes>...</Attributes>  
   <Hierarchies>...</Hierarchies>  
      <Annotations>...</Annotation>  
</CubeDimension>  
```  
  
## <a name="data-type-characteristics"></a>資料類型特性  
  
|特性|說明|  
|--------------------|-----------------|  
|基底資料類型|無|  
|衍生資料類型|無|  
  
## <a name="data-type-relationships"></a>資料類型關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|無|  
|子元素|[AllMemberAggregationUsage](../../../analysis-services/scripting/properties/allmemberaggregationusage-element-assl.md)，[註解](../../../analysis-services/scripting/collections/annotations-element-assl.md)，[屬性](../../../analysis-services/scripting/collections/attributes-element-assl.md)， [DimensionID](../../../analysis-services/scripting/properties/dimensionid-element-assl.md)，[階層](../../../analysis-services/scripting/collections/hierarchies-element-assl.md)， [HierarchyUniqueNameStyle](../../../analysis-services/scripting/properties/hierarchyuniquenamestyle-element-assl.md)，[識別碼](../../../analysis-services/scripting/properties/id-element-assl.md)， [MemberUniqueNameStyle](../../../analysis-services/scripting/properties/memberuniquenamestyle-element-assl.md)，[名稱](../../../analysis-services/scripting/properties/name-element-assl.md)，[可見](../../../analysis-services/scripting/properties/visible-element-assl.md)，[翻譯](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|衍生的元素|[維度](../../../analysis-services/scripting/objects/dimension-element-assl.md)([維度](../../../analysis-services/scripting/collections/dimensions-element-assl.md)集合[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>備註  
 有一個**CubeDimension**每個維度關聯性上**Cube**。 **CubeDimension**涵蓋所有**MeasureGroups**的 cube。  
  
 A **CubeDimension**必須包含[CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)如果維度與階層的特定項目，包括停用階層 （因而，允許的選取範圍階層要套用至特定維度使用方式），或變成不可見的階層。  
  
 同樣地， **CubeDimension**必須包含[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)前提維度與屬性特定項目。 (沒有任何方法可選取要套用至特定維度使用方式的屬性，不過您可以讓屬性隱藏)。  
  
 分析管理物件 (AMO) 物件模型中的對應元素是<xref:Microsoft.AnalysisServices.CubeDimension>。  
  
## <a name="see-also"></a>請參閱＜  
 [Analysis Services 指令碼語言 XML 資料類型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
