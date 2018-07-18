---
title: Session 元素 (XMLA) |Microsoft 文件
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 02b4c93919e6354a59aad9b42a4f6dc8373c880f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34577500"
---
# <a name="session-element-xmla"></a>Session 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  在 SOAP 要求訊息中使用 SOAP 標頭，來識別現有的明確工作階段上的 Analysis Services 執行個體。  
  
 **命名空間**描述 urn:-microsoft-schemas-microsoft-com:-分析  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
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
  
|特性|描述|  
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
  
|attribute|描述|  
|---------------|-----------------|  
|SessionId|需要**字串**屬性，可識別要使用工作階段。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會使用全域唯一識別碼 (GUID) 來識別工作階段。|  
  
## <a name="remarks"></a>備註  
 **工作階段**標頭項目上識別現有且明確啟動工作階段[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]執行個體。 **工作階段**項目是在下列類型的訊息的 SOAP 標頭的一部分：  
  
-   SOAP 回應，其中包含[BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) SOAP 標頭項目。  
  
-   識別要執行的工作階段的 SOAP 要求[探索](../../../analysis-services/xmla/xml-elements-methods-discover.md)或[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)方法。  
  
 工作階段識別碼並不保證工作階段會維持有效狀態。 指定的工作階段**工作階段**項目可能會過期。 例如，如果工作階段逾時或是與工作階段有關的連接中斷，則此工作階段可能會過期。 如果此工作階段過期而不再有效，則 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會結束此工作階段，並回復目前進行中的任何交易。 與不再有效的工作階段識別碼一起傳送的任何 SOAP 訊息都會失敗，而且會出現一個 SOAP 錯誤，表示找不到指定的工作階段。  
  
 如果**工作階段**項目不會傳送 SOAP 要求，一部分[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]執行個體會以隱含方式開始的工作階段的持續時間**探索**或**Execute**方法呼叫中，然後再結束方法呼叫完成該工作階段。  
  
## <a name="see-also"></a>另請參閱
 [EndSession 元素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [管理連接與工作階段&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [標頭&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
