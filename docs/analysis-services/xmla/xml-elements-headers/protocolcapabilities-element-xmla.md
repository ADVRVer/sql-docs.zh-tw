---
title: "ProtocolCapabilities 元素 (XMLA) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
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
apiname: ProtocolCapabilities Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.protocolcapabilities
- http://schemas.microsoft.com/analysisservices/2003/engine#ProtocolCapabilities
- urn:schemas-microsoft-com:xml-analysis#ProtocolCapabilities
helpviewer_keywords: ProtocolCapabilities element
ms.assetid: f923896a-3f32-46a3-9543-388c30b3465d
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bac8f7dccd818128280dc532f276379050c69a77
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="protocolcapabilities-element-xmla"></a>ProtocolCapabilities 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]在 SOAP 要求訊息中使用 SOAP 標頭，以識別執行個體之間的通訊協定功能[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]和用戶端應用程式。  
  
 **命名空間**`http://schemas.microsoft.com/analysisservices/2003/engine`  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <ProtocolCapabilities xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
         <Capability>...</Capability>  
      </ProtocolCapabilities>  
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
|子元素|[功能](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>備註  
 **ProtocolCapabilities**項目可讓用戶端應用程式與交涉通訊協定的功能，例如二進位 XML 或壓縮支援[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]在任何時間的執行個體。 通訊協定交涉包含下列步驟：  
  
1.  用戶端應用程式透過傳送包含 **ProtocolCapabilities** 元素當做 SOAP 標頭一部分的 SOAP 要求，識別其通訊協定功能。  
  
2.  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體收到並處理此 SOAP 要求。  
  
3.  如果[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]執行個體的要求相同通訊協定功能，執行個體會傳送包含相同的 SOAP 回應**ProtocolCapabilities**傳送 SOAP 要求中的項目，且已通訊協定成功交涉。 否則，通訊協定功能不會成功交涉，而且此執行個體會傳回 SOAP 錯誤。  
  
 成功交涉通訊協定功能，多久用戶端應用程式之後，[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]依據工作階段是明確或隱含的執行個體使用特定的通訊協定而定：  
  
-   為明確工作階段是使用建立[BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)標頭項目。 若為明確工作階段，交涉的通訊協定就會一直使用到用戶端應用程式傳送新的 **ProtocolCapabilities** 元素或工作階段結束為止。  
  
-   隱含工作階段是指 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體所建立而且用戶端應用程式在提交 SOAP 要求時並未明確指定的工作階段。 若為隱含工作階段，交涉的通訊協定就只會使用到 SOAP 要求完成為止。  
  
 通訊協定功能不需要明確交涉。 也就是說，用戶端應用程式不需要在 SOAP 要求中包含 **ProtocolCapabilities** 元素。 如果 SOAP 要求不包含**ProtocolCapabilities**項目，[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]執行個體使用相同的格式與 SOAP 要求的回應。  
  
## <a name="see-also"></a>請參閱  
 [管理連接和工作階段 &#40;XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [標頭 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
