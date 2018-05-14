---
title: EndSession 元素 (XMLA) |Microsoft 文件
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d086e93de6030621356271582d8162e58fcabe4f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="endsession-element-xmla"></a>EndSession 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  在 SOAP 要求訊息中會使用 SOAP 標頭，結束執行個體上現有的工作階段[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]。  
  
 **命名空間**描述 urn:-microsoft-schemas-microsoft-com:-分析  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <EndSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
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
|父元素|無|  
|子元素|無|  
  
## <a name="attributes"></a>屬性  
  
|Attribute|Description|  
|---------------|-----------------|  
|SessionId|需要**字串**屬性，可識別要結束工作階段。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會使用全域唯一識別碼 (GUID) 來識別工作階段。|  
  
## <a name="remarks"></a>備註  
 **EndSession** SOAP 要求傳送到現有且明確啟動工作階段上的標頭元素屬於[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]執行個體。 如果**EndSession** 、 標頭元素已傳送，但是包含不再有效的工作階段識別碼，表示找不到工作階段傳回 SOAP 錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [BeginSession 元素 & #40;XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)   
 [Session 元素 & #40;XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [管理連接和工作階段 & #40;XMLA & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [標頭 & #40;XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
