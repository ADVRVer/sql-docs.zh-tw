---
title: "Detach 元素 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: Detach command
ms.assetid: adbc7920-2a4a-4842-9e6f-37006fa19ff8
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ea4251624e848666f513c57e23d299e735ee8f5f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="detach-element"></a>Detach 元素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]卸離[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]從目前的伺服器執行個體的資料庫。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Command>  
   <Detach>  
      <Object>...</Object>  
      <Password>...</Password>  
   </Detach>  
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
|子元素|[物件](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)<br /><br /> [[密碼]](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md)|  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Attach 元素](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [附加和卸離 Analysis Services 資料庫](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [移動 Analysis Services 資料庫](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [資料庫 Readwritemode](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [切換 ReadOnly 和 ReadWrite 模式之間的 Analysis Services 資料庫](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
