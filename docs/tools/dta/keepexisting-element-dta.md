---
title: "KeepExisting 元素 (DTA) |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1277619f7c7f293ad49724f40faa9eb0cbb64cf1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="keepexisting-element-dta"></a>KeepExisting 元素 (DTA)
  指定在產生建議時，Database Engine Tuning Advisor 必須保留的實體設計結構 (索引、索引檢視或資料分割)。  
  
## <a name="syntax"></a>語法  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|**資料類型和長度**|**string**，伺服器強制實施長度限制。|  
|**允許的值**|**NONE**<br /> 無現有結構。<br /><br /> **ALL**<br /> 所有現有結構。<br /><br /> **ALIGNED**<br /> 所有資料分割對齊結構。<br /><br /> **CL_IDX**<br /> 資料表的所有叢集索引。<br /><br /> **IDX**<br /> 資料表的所有叢集和非叢集索引。<br /><br /> 這個元素只能使用這些值的其中之一。|  
|**預設值**|無。|  
|**出現次數**|選擇性。 每個 **TuningOptions** 元素只能使用這個元素一次。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[TuningOptions 元素 &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**子元素**|無。|  
  
## <a name="example"></a>範例  
 如需此元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
