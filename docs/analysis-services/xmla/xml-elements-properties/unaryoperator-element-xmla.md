---
title: UnaryOperator 元素 (XMLA) |Microsoft 文件
ms.custom: ''
ms.date: 03/17/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- UnaryOperator Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#UnaryOperator
- urn:schemas-microsoft-com:xml-analysis#UnaryOperator
- microsoft.xml.analysis.unaryoperator
helpviewer_keywords:
- UnaryOperator element
ms.assetid: 4dc9cfbe-6f8b-42bc-8d3a-42f48ca5d299
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 125f56ea405828aea8a89bd6a7d882991b16d752
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="unaryoperator-element-xmla"></a>UnaryOperator 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  包含父代所代表之屬性成員的一元運算子[屬性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Attribute>  
   ...  
   <UnaryOperator>...</UnaryOperator>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[屬性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 **UnaryOperator**元素包含定義父代所定義之屬性成員的一元運算子的多維度運算式 (MDX) 運算式**屬性**項目。  
  
 如需有關 MDX 運算式的詳細資訊，請參閱[運算式 & #40;MDX & #41;](../../../mdx/expressions-mdx.md).  
  
## <a name="see-also"></a>另請參閱  
 [插入項目 & #40;XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Update 元素 & #40;XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [屬性 & #40;XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
