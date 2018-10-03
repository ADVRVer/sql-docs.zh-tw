---
title: ModelingFlags 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ModelingFlags Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ModelingFlags
helpviewer_keywords:
- ModelingFlags element
ms.assetid: 83968c1e-aae8-4657-aa53-d971de0dc834
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 369af68b69c25d70ea80096947a0ecda4488418a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063258"
---
# <a name="modelingflags-element-assl"></a>ModelingFlags 元素 (ASSL)
  包含的集合[ModelingFlag](../objects/modelingflag-element-assl.md)中的資料行的項目[MiningStructure](../objects/miningstructure-element-assl.md)或是[MiningModel](../objects/miningmodel-element-assl.md)。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<MiningModelColumn> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <ModelingFlags>  
      <ModelingFlag xsi:type="MiningModelingFlag">...</ModelingFlag>  
   </ModelingFlags>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|None|  
|預設值|None|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)， [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|子元素|[ModelingFlag](../objects/modelingflag-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 在 「 分析管理物件 (AMO) 物件模型的對應元素是<xref:Microsoft.AnalysisServices.MiningModelingFlags>。  
  
## <a name="see-also"></a>另請參閱  
 [集合&#40;ASSL&#41;](collections-assl.md)  
  
  
