---
title: "CustomRollupColumn 元素 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: CustomRollupColumn Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CustomRollupColumn
helpviewer_keywords: CustomRollupColumn element
ms.assetid: 8c825f16-0d17-4ff8-bc18-b52cf11edba7
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9cd1d65acab0ca701e77fbec10371ddf0ad97366
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="customrollupcolumn-element-assl"></a>CustomRollupColumn 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]定義提供自訂積存公式之資料行的詳細資料。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <CustomRollupColumn xsi:type="DataItem">...</CustomRollupColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 如需有關**DataItem**型別，包括 Analysis Services 指令碼語言 (ASSL) 物件和屬性的資料表**DataItem**類型，請參閱[DataItem 資料類型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 對應目的父代的項目**CustomRollupColumn**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.DimensionAttribute>。  
  
## <a name="see-also"></a>請參閱  
 [物件 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
