---
title: "NamingTemplateTranslation 元素 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NamingTemplateTranslation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NamingTemplateTranslation
helpviewer_keywords:
- NamingTemplateTranslation element
ms.assetid: 4a97a31d-23bc-4afd-a4dc-bc0ad7121f08
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa966a46acf8f6ce0c40b7c2ffb341552afa4e99
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="namingtemplatetranslation-element-assl"></a>NamingTemplateTranslation 元素 (ASSL)
  提供當地語系化的翻譯的[NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)父項目[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)資料型別。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|[轉譯](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[NamingTemplateTranslations](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 值**NamingTemplateTranslation**項目僅供父屬性 (換言之，值[使用量](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)元素**DimensionAttribute**父代設定為*父*) 來儲存的當地語系化的翻譯**NamingTemplate**給定語言的值。  
  
 對應目的父代的項目**NamingTemplateTranslations**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.DimensionAttribute>。  
  
## <a name="see-also"></a>另請參閱  
 [NamingTemplate 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)   
 [物件 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
