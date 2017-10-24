---
title: "DTAInput 元素 (DTA) |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 22a7b07a5dee4e826d2b438d384d44796ca23480
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="dtainput-element-dta"></a>DTAInput 元素 (DTA)
  包含 Database Engine Tuning Advisor 的 XML 輸入定義。  
  
## <a name="syntax"></a>語法  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|---------------------|-----------------|  
|**資料類型和長度**|無。|  
|**預設值**|無。|  
|**出現次數**|每個 **DTAXML** 元素可以選擇性地使用這個元素一次。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[DTAXML 元素 &#40; Dta& &#41;](../../tools/dta/dtaxml-element-dta.md)|  
|**子元素**|[Server 元素 &#40; Dta& &#41;](../../tools/dta/server-element-dta.md)<br /><br /> [Workload 元素 &#40; Dta& &#41;](../../tools/dta/workload-element-dta.md)<br /><br /> [TuningOptions 元素 &#40; Dta& &#41;](../../tools/dta/tuningoptions-element-dta.md)<br /><br /> [Configuration 元素 &#40; Dta& &#41;](../../tools/dta/configuration-element-dta.md)|  
  
## <a name="remarks"></a>備註  
 這個元素是 Database Engine Tuning Advisor 輸入結構描述階層的根。 Database Engine Tuning Advisor 的輸入可以是指定資料庫需要微調之伺服器、工作負載、微調選項或使用者指定組態的引數。  
  
## <a name="example"></a>範例  
 如需 **DTAInput** 元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 輸入檔參考 &#40;Database Engine Tuning Advisor&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

