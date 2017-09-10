---
title: "ID 元素 (XMLA) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ID
- urn:schemas-microsoft-com:xml-analysis#ID
- microsoft.xml.analysis.id
helpviewer_keywords:
- ID element
ms.assetid: f7d67599-6a70-4455-bfdb-1d127e5eff4e
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7dcd7bd4904ae4cc3ae2b8a8e3345af52016563
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="id-element-xmla"></a>ID 元素 (XMLA)
  識別要在上面執行父代的鎖定[鎖定](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)或[Unlock](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Lock> <!-- or Unlock>  
   ...  
   <ID>...</ID>  
   ...  
</Lock>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[鎖定](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)，[解除鎖定](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 **識別碼**元素包含用來識別鎖定的全域唯一識別碼 (GUID)。  
  
## <a name="see-also"></a>另請參閱  
 [Object 元素 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Mode 元素 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md)   
 [屬性 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
