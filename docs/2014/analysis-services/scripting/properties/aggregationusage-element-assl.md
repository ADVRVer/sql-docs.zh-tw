---
title: AggregationUsage 元素 (ASSL) |Microsoft 文件
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
- AggregationUsage Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationUsage
helpviewer_keywords:
- AggregationUsage element
ms.assetid: af0c2e7f-b659-4fbf-9b1a-66128db669a2
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0cc9d13ed663b92224584ab57f6f467e3a472d8e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36029903"
---
# <a name="aggregationusage-element-assl"></a>AggregationUsage 元素 (ASSL)
  控制項如何在彙總設計師[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]設計彙總。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CubeAttribute>  
   ...  
   <AggregationUsage>...</AggregationUsage>  
   ...  
</CubeAttribute>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|字串 (列舉)|  
|預設值|*預設值*|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 這個元素的值限制為下表所列的其中一個字串。  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|*Full*|此 Cube 的每一個彙總都必須包含這個屬性。|  
|*無*|此 Cube 不應該有任何彙總包含這個屬性。|  
|*不受限制*|彙總設計師沒有任何限制。|  
|*預設值*|彙總設計師會套用預設規則根據屬性的型別 (*完整*代表索引鍵， *Unrestricted*供其他人)。|  
  
 在「分析管理物件」(AMO) 物件模型中對應至 `AggregationUsage` 允許值的列舉是 <xref:Microsoft.AnalysisServices.AggregationUsage>。  
  
## <a name="see-also"></a>另請參閱  
 [Cube 元素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  