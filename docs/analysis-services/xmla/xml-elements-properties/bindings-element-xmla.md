---
title: "繫結元素 (XMLA) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Bindings Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.bindings
- urn:schemas-microsoft-com:xml-analysis#Bindings
- http://schemas.microsoft.com/analysisservices/2003/engine#Bindings
helpviewer_keywords: Bindings element
ms.assetid: caa34cab-f61f-4f39-b800-af1601714daa
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dca8212ff215707f6fca0a724ba63cf90ea93e30
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="bindings-element-xmla"></a>Bindings 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]包含集合[繫結](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md)父元素之[批次](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)或[程序](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Batch> <!-- or Process>  
...  
   <Bindings>  
      <Binding>...</Binding>  
   </Bindings>  
...  
</Alter>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[批次](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)，[程序](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|子元素|[繫結](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md)|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [屬性 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
