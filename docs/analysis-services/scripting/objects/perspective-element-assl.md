---
title: Perspective 元素 (ASSL) |Microsoft 文件
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d84b369134c55a09317ae8812f2d511e147605bf
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="perspective-element-assl"></a>Perspective 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  定義檢視方塊的詳細資料[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Perspectives>  
   <<Perspective>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DefaultMeasure>...</DefaultMeasure>  
      <Dimensions>...</Dimensions>  
            <MeasureGroups>...</MeasureGroups>  
      <Calculations>...</Calculations>  
      <Kpis>...</Kpis>  
            <Actions>...</Actions>  
      <Annotations>...</Annotations>  
   </Perspective>  
</Perspectives>  
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
|父元素|[檢視方塊](../../../analysis-services/scripting/collections/perspectives-element-assl.md)|  
|子元素|[動作](../../../analysis-services/scripting/collections/actions-element-assl.md)，[註解](../../../analysis-services/scripting/collections/annotations-element-assl.md)，[計算](../../../analysis-services/scripting/collections/calculations-element-assl.md)， [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)， [DefaultMeasure](../../../analysis-services/scripting/properties/defaultmeasure-element-assl.md)， [描述](../../../analysis-services/scripting/properties/description-element-assl.md)，[維度](../../../analysis-services/scripting/collections/dimensions-element-assl.md)，[識別碼](../../../analysis-services/scripting/properties/id-element-assl.md)， [Kpi](../../../analysis-services/scripting/collections/kpis-element-assl.md)， [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)， [MeasureGroups](../../../analysis-services/scripting/collections/measuregroups-element-assl.md)，[名稱](../../../analysis-services/scripting/properties/name-element-assl.md)，[翻譯](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 檢視方塊會提供 Cube 的子集，以便選取要包含的維度、階層、屬性和其他詳細資料，以及定義要包含的資料配量。 檢視方塊是由單一 Cube 所擁有。 您無法在檢視方塊內部覆寫或加入物件。所有維度、階層和其他詳細資料都必須存在基礎 Cube 中。 此外，您也無法加入物件並將它們標示為不顯示。  
  
 分析管理物件 (AMO) 物件模型中的對應元素是<xref:Microsoft.AnalysisServices.Perspective>。  
  
## <a name="see-also"></a>另請參閱  
 [物件 & #40;ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
