---
title: "ForeignKeyColumn 元素 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ForeignKeyColumn Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ForeignKeyColumn
helpviewer_keywords: ForeignKeyColumn element
ms.assetid: 6c00dcc6-8d5b-4293-8b72-c7a22e298c8d
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e12c99ec386c2cd6829bf2ca1664055a33a1b5ba
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="foreignkeycolumn-element-assl"></a>ForeignKeyColumn 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]識別關聯式資料來源之父資料表的聯結。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<ForeignKeyColumns>  
   <ForeignKeyColumn xsi:type="DataItem">...</ForeignKeyColumn>  
</ForeignKeyColumns>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|預設值|無|  
|基數|0-n：出現一次以上的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[ForeignKeyColumns](../../../analysis-services/scripting/collections/foreignkeycolumns-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 如需有關**DataItem**型別，包括 Analysis Services 指令碼語言 (ASSL) 物件和屬性的資料表**DataItem**類型，請參閱[DataItem 資料類型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 對應目的父代的項目**ForeignKeyColumns**分析管理物件 (AMO) 物件模型中的集合是<xref:Microsoft.AnalysisServices.TableMiningStructureColumn>。  
  
## <a name="see-also"></a>請參閱  
 [TableMiningStructureColumn 資料類型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)   
 [MiningStructureColumn 資料類型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)   
 [MiningStructure 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [物件 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
