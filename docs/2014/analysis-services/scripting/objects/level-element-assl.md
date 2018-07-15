---
title: Level 元素 (ASSL) |Microsoft Docs
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
- Level Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LEVEL
helpviewer_keywords:
- Level element
ms.assetid: 66ee2c16-d6b8-4dd3-879f-1f2b6923bc43
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ba9ca10d1d3ad2319e451d6008c6e8ad77078fc7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263874"
---
# <a name="level-element-assl"></a>Level 元素 (ASSL)
  定義中的層級[階層](hierarchy-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Levels>  
      <Level>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <SourceAttributeID>...</SourceAttributeID>  
      <HideMemberIf>...</HideMemberIf>  
      <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Level>  
</Levels>  
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
|父元素|[Levels](../collections/levels-element-assl.md)|  
|子元素|[註釋](../collections/annotations-element-assl.md)，[描述](../properties/description-element-assl.md)， [HideMemberIf](../properties/hidememberif-element-assl.md)，[識別碼](../properties/id-element-assl.md)，[名稱](../properties/name-element-assl.md)， [SourceAttributeID](../properties/attributeid-element-assl.md)，[翻譯](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 此資料類型在任何部署模式 (1-多維度和資料採礦、2-SharePoint 及 3-表格式) 下都沒有限制。  
  
 在 「 分析管理物件 (AMO) 物件模型的對應元素是<xref:Microsoft.AnalysisServices.Level>。  
  
## <a name="see-also"></a>另請參閱  
 [物件&#40;ASSL&#41;](objects-assl.md)  
  
  
