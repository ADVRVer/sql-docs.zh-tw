---
title: Collation 元素 (ASSL) |Microsoft Docs
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
- Collation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Collation
helpviewer_keywords:
- Collation element
ms.assetid: 9b6dbe19-543e-43e6-abe9-1e8b4dfaa275
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 92e4e7eaa9eb4d994fc225c9d3d1c9a0c941b1b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213928"
---
# <a name="collation-element-assl"></a>Collation 元素 (ASSL)
  決定父元素所使用的定序。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Database> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Collation>...</Collation>  
   ...  
</Database>  
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
|父元素|[Cube](../objects/cube-element-assl.md)，[資料庫](../objects/database-element-assl.md)， [DataItem](../data-type/dataitem-data-type-assl.md)，[維度](../objects/dimension-element-assl.md)， [MiningModel](../objects/miningmodel-element-assl.md)， [MiningStructure](../objects/miningstructure-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 `Collation` 字串包含地區設定識別碼 (LCID) 和比較旗標 (以底線字元隔開)。 例如，Latin1_General_CI_AS 是可接受的字串。  
  
 在「分析管理物件」(AMO) 物件模型中對應至 `Collation` 父系的元素是 <xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.Database>、<xref:Microsoft.AnalysisServices.DataItem>、<xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.MiningModel> 和 <xref:Microsoft.AnalysisServices.MiningStructure>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
