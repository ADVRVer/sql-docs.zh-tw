---
title: RollbackTransaction 元素 (XMLA) |Microsoft 文件
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d1bf63b2e3db0add86927c2f624a01fafa31e3d7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574500"
---
# <a name="rollbacktransaction-element-xmla"></a>RollbackTransaction 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  上的 Analysis Services 執行個體的目前工作階段的交易回復。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Command>  
   <RollbackTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-n：出現一次以上的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 **RollbackTransaction**命令會回復所有使用中交易，使用明確定義**BeginTransaction**項目，目前工作階段上的。 如果使用中交易尚未存在，就會發生錯誤。 如果使用中交易已經存在，[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體就會將目前工作階段之交易的參考計數遞減至零，並回復所有使用中交易。  
  
## <a name="see-also"></a>另請參閱
 [BeginTransaction 元素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)   
 [Cancel 元素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [CommitTransaction 元素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [命令&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
