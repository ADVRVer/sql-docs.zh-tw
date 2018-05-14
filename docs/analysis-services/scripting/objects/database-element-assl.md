---
title: Database 元素 (ASSL) |Microsoft 文件
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 55636b5ea679bb9d811204f45be914751ceb5c1c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="database-element-assl"></a>Database 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  定義[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]資料庫。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Databases>  
   <Database>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastUpdate>...</LastUpdate>  
      <Description>...</Description>  
      <State>   </State>  
      <AggregationPrefix>...</AggregationPrefix>  
      <EstimatedSize>...</EstimatedSize>  
      <LastProcessed>...</LastProcessed>  
      <Language>...</Language>  
            <Collation>...</Collation>  
      <Visible>...</Visible>  
      <MasterDatasourceID>...</MasterDataSourceID>  
      <Accounts>...</Accounts>  
      <DataSources>...</DataSources>  
      <DataSourceViews>...</DataSourceViews>  
      <Dimensions>...</Dimensions>  
      <Cubes>...</Cubes>  
      <MiningStructures>...</MiningStructures>  
            <Roles>...</Roles>  
      <Assemblies>...</Assemblies>  
      <DatabasePermissions>...</DatabasePermissions>  
            <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Database>  
</Databases>  
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
|父元素|[資料庫](../../../analysis-services/scripting/collections/databases-element-assl.md)|  
|子元素|[帳戶](../../../analysis-services/scripting/collections/accounts-element-assl.md)， [AggregationPrefix](../../../analysis-services/scripting/properties/aggregationprefix-element-assl.md)，[註解](../../../analysis-services/scripting/collections/annotations-element-assl.md)，[組件](../../../analysis-services/scripting/collections/assemblies-element-assl.md)，[定序](../../../analysis-services/scripting/properties/collation-element-assl.md)， [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)， [Cube](../../../analysis-services/scripting/collections/cubes-element-assl.md)， [DatabasePermissions](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md)， [DataSources](../../../analysis-services/scripting/collections/datasources-element-assl.md)， [DataSourceViews](../../../analysis-services/scripting/collections/datasourceviews-element-assl.md)，[描述](../../../analysis-services/scripting/properties/description-element-assl.md)，[維度](../../../analysis-services/scripting/collections/dimensions-element-assl.md)， [EstimatedSize](../../../analysis-services/scripting/properties/estimatedsize-element-assl.md)，[識別碼](../../../analysis-services/scripting/properties/id-element-assl.md)，[語言](../../../analysis-services/scripting/properties/language-element-assl.md)， [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md)， [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)， [LastUpdate](../../../analysis-services/scripting/properties/lastupdate-element-assl.md)， [MasterDatasourceID](../../../analysis-services/scripting/properties/masterdatasourceid-element-assl.md)， [MiningStructures](../../../analysis-services/scripting/collections/miningstructures-element-assl.md)，[名稱](../../../analysis-services/scripting/properties/name-element-assl.md)，[角色](../../../analysis-services/scripting/collections/roles-element-assl.md)，[狀態](../../../analysis-services/scripting/properties/state-element-assl.md)，[翻譯](../../../analysis-services/scripting/collections/translations-element-assl.md)，[可見](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 分析管理物件 (AMO) 物件模型中的對應元素是<xref:Microsoft.AnalysisServices.Database>。  
  
## <a name="see-also"></a>另請參閱  
 [Server 元素 & #40;ASSL & #41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [物件 & #40;ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
