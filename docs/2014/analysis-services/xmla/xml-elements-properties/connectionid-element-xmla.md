---
title: ConnectionID 元素 (XMLA) |Microsoft Docs
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
- ConnectionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ConnectionID
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionID
- microsoft.xml.analysis.connectionid
helpviewer_keywords:
- ConnectionID element
ms.assetid: de044fb2-f713-46b2-8899-14e8d515e823
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eb5a4c5a358c3be6629d579c140cb2407e74b838
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265284"
---
# <a name="connectionid-element-xmla"></a>ConnectionID 元素 (XMLA)
  識別作用中的連線要在上面執行父代[取消](../xml-elements-commands/cancel-element-xmla.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Cancel>  
   ...  
   <ConnectionID>...</ConnectionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|Integer|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[取消](../xml-elements-commands/cancel-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [CancelAssociated 元素&#40;XMLA&#41;](cancelassociated-element-xmla.md)   
 [SessionID 元素&#40;XMLA&#41;](id-element-xmla.md)   
 [SPID 元素&#40;XMLA&#41;](spid-element-xmla.md)   
 [屬性&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
