---
title: root 元素 (XMLA) |Microsoft 文件
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f4fc4072c7b19cff327463dd8df8af7d136e6c1e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="root-element-xmla"></a>root 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  包含所傳回的結果[探索](../../../analysis-services/xmla/xml-elements-methods-discover.md)方法或 XML for Analysis (XMLA) 命令，使用執行[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)方法。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<return> <!-- or results-->  
   ...  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">...</root> <!-- for Execute method only -->  
   <!-- or -->  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">...</root>  
   <!-- or -->  
   <root xmlns= xmlns="urn:schemas-microsoft-com:xml-analysis:empty">...</root>  
   ...  
</return>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|請參閱下表。|  
|預設值|無|  
|基數|1-n：出現一次以上的必要元素。|  
  
|Ancestor|資料類型|  
|--------------|---------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[資料列集](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)， [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)，[資料列集](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)， [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[結果](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)，[傳回](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 **根**項目包含在傳回的資訊[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)傳回單一項目**探索**方法呼叫，或在[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)單一所執行的單一 XMLA 命令所傳回的項目**Execute**方法呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [屬性 & #40;XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
