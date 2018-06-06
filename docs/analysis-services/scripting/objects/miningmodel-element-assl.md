---
title: MiningModel 元素 (ASSL) |Microsoft 文件
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e3de4138f69df9cfaebb0d726bc9fac27dcbf629
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="miningmodel-element-assl"></a>MiningModel 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  定義單一資料採礦模型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<MiningModels>  
      <MiningModel>  
      <Name>...</Name>  
            <ID>...</ID>  
      <Description>...</<Descrip  
            <Algorithm>...</Algorithm>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <AlgorithmParameters>...</AlgorithmParameters>  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <Translations>...</Translations>  
      <Columns>...</Columns>  
      <State>...</State>  
      <MiningModelPermissions>...</MiningModelPermissions>  
      <Language>...</Language>  
            <Collation>...</Collation>  
            <Annotations>...</Annotations>  
            <ddl100_100:FoldingParameters>   </FoldingParameters>  
   </MiningModel>  
</MiningModels>  
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
|父元素|[MiningModels](../../../analysis-services/scripting/collections/miningmodels-element-assl.md)|  
|子元素|[演算法](../../../analysis-services/scripting/properties/algorithm-element-assl.md)， [AlgorithmParameters](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)， [AllowDrillThrough](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)，[註解](../../../analysis-services/scripting/collections/annotations-element-assl.md)，[定序](../../../analysis-services/scripting/properties/collation-element-assl.md)， [資料行](../../../analysis-services/scripting/collections/columns-element-assl.md)， [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)，[描述](../../../analysis-services/scripting/properties/description-element-assl.md)，[識別碼](../../../analysis-services/scripting/properties/id-element-assl.md)，[語言](../../../analysis-services/scripting/properties/language-element-assl.md)， [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md)， [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)， [MiningModelPermissions](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md)，[名稱](../../../analysis-services/scripting/properties/name-element-assl.md)，[狀態](../../../analysis-services/scripting/properties/state-element-assl.md)， [翻譯](../../../analysis-services/scripting/collections/translations-element-assl.md)，<br /><br /> [FoldingParameters](../../../analysis-services/scripting/properties/foldingparameters-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 **FoldingParameters**採礦模型的項目是伺服器，供內部使用，且不支援用於 DDL 陳述式。  
  
 分析管理物件 (AMO) 物件模型中的對應元素是<xref:Microsoft.AnalysisServices.MiningModel>。  
  
## <a name="see-also"></a>另請參閱  
 [物件 & #40;ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
