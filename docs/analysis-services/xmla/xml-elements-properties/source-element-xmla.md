---
title: Source 元素 (XMLA) |Microsoft 文件
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8aaef002e649e01a51b99bd007ae5459e8cdbd97
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576420"
---
# <a name="source-element-xmla"></a>Source 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  表示要合併期間的來源資料分割[MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)命令。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Sources>  
   <Source>  
      <DatabaseID>...</DatabaseID>  
      <CubeID>...</CubeID>  
      <MeasureGroupID>...</MeasureGroupID>  
      <PartitionID>...</PartitionID>  
   </Source>  
</Sources>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|1-n：出現一次以上的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[來源](../../../analysis-services/xmla/xml-elements-properties/sources-element-xmla.md)|  
|子元素|[CubeID](../../../analysis-services/xmla/xml-elements-properties/cubeid-element-xmla.md)， [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md)， [MeasureGroupID](../../../analysis-services/xmla/xml-elements-properties/measuregroupid-element-xmla.md)， [PartitionID](../../../analysis-services/xmla/xml-elements-properties/partitionid-element-xmla.md)|  
  
## <a name="remarks"></a>備註  
 **來源**項目是單一資料分割合併到目標資料分割所指定的物件參考**目標**父元素之**MergePartitions**項目。  
  
## <a name="example"></a>範例  
 下列範例會將 `Internet Sales` 量值群組的四個資料分割都結合至 `Internet_Sales_2004` 目標資料分割中。 此範例會參考**Adventure Works** cube[!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)]範例[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]資料庫。  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
     <Source>        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>        <CubeID>Adventure Works</CubeID>        <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>        <PartitionID>Internet_Sales_2001</PartitionID>     </Source>     <Source>        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>        <CubeID>Adventure Works</CubeID>      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>      <PartitionID>Internet_Sales_2002</PartitionID>    </Source>    <Source>      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>      <PartitionID>Internet_Sales_2003</PartitionID>    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>另請參閱
 [目標項目&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)   
 [屬性&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
