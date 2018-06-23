---
title: ProcessingMode 元素 (ASSL) |Microsoft 文件
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
- ProcessingMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ProcessingMode
helpviewer_keywords:
- ProcessingMode element
ms.assetid: dff6eeba-f09c-4d8c-ad81-caef76254af0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a4f302608db355a639d9fb82e024a7a72cf560b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36033343"
---
# <a name="processingmode-element-assl"></a>ProcessingMode 元素 (ASSL)
  指出此執行個體應該在處理期間或處理之後進行索引和彙總。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <ProcessingMode>...</ProcessingMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|字串 (列舉)|  
|預設值|*規則*|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[Cube](../objects/cube-element-assl.md)，[維度](../objects/dimension-element-assl.md)， [MeasureGroup](../objects/group-element-assl.md)，[磁碟分割](../objects/partition-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 `ProcessingMode` 上的 `Cube` 值會提供預設值給 Cube，而且您可以透過設定每個資料分割的 `ProcessingMode`，覆寫此值。  
  
 這個元素的值限制為下表所列的其中一個字串。  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|*規則*|此執行個體會在處理期間建立索引並執行彙總。|  
|*LazyOptimizations*|此執行個體會在處理之後建立索引並執行彙總。|  
  
 在「分析管理物件」(AMO) 物件模型中對應至 `ProcessingMode` 允許值的列舉是 <xref:Microsoft.AnalysisServices.ProcessingMode>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  