---
title: "IsAggregatable 元素 (ASSL) |Microsoft 文件"
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
apiname: IsAggregatable Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: IsAggregatable
helpviewer_keywords: IsAggregatable element
ms.assetid: ed7dbe89-259c-4c5c-9660-b965c3af1573
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2a40d33451ac36edc848f1d66eecd2ea21c3b2dc
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="isaggregatable-element-assl"></a>IsAggregatable 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]指定是否值[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)項目可以彙總。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<DimensionAttribute>  
      ...  
   <IsAggregatable>...</IsAggregatable>  
  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|布林|  
|預設值|True|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 對應目的父代的項目**IsAggregatable**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.DimensionAttribute>。  
  
## <a name="see-also"></a>請參閱  
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
