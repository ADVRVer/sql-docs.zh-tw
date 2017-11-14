---
title: "AggregationDesignID 元素 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
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
apiname:
- AggregationDesignID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationDesignID
helpviewer_keywords:
- AggregationDesignID element
ms.assetid: e7f1f7ae-3169-4c0c-aadb-f7465155d652
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cc9f80f42ff99cd0f199e746a25ec7cf5595b700
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="aggregationdesignid-element-assl"></a>AggregationDesignID 元素 (ASSL)
  識別[AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)元素相關聯[分割](../../../analysis-services/scripting/objects/partition-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Partition>  
      ...  
   <AggregationDesignID>...</AggregationDesignID>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[資料分割](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 對應目的父代的項目**AggregationDesignID**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.Partition>。 另請參閱<xref:Microsoft.AnalysisServices.AggregationDesign>。  
  
## <a name="see-also"></a>另請參閱  
 [AggregationDesign 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)   
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

