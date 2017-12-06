---
title: "FeatureSet 元素 (DTA) |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4b31e99ca6ad7d26ae67bd3092295cc7736d1fa
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2017
---
# <a name="featureset-element-dta"></a>FeatureSet 元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]包含您想要 Database Engine Tuning Advisor 在分析期間所使用的實體設計結構 （索引或索引檢視表）。  
  
## <a name="syntax"></a>語法  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|**資料類型和長度**|**字串**，沒有最大長度。|  
|**允許的值**|**IDX_IV**<br /> 索引和索引檢視表。<br /><br /> **IDX**<br /> 只有索引。<br /><br /> **IV**<br /> 只有索引檢視表。<br /><br /> **NCL_IDX**<br /> 只有非叢集索引。<br /><br /> 這個元素使用這些值的其中之一。|  
|**預設值**|**IDX**|  
|**出現次數**|每個 **TuningOptions** 元素都需要一次，除非使用 **DropOnlyMode** 元素。 如果使用 **DropOnlyMode** ，您不能使用 **FeatureSet**。 這些元素互斥。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[TuningOptions 元素 &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**子元素**|無。|  
  
## <a name="example"></a>範例  
 如需此元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md)。  
  
## <a name="see-also"></a>請參閱  
 [XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
