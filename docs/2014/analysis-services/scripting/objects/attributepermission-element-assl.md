---
title: AttributePermission 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributePermission
helpviewer_keywords:
- AttributePermission element
ms.assetid: efc8aa63-3959-4b2e-98f8-2a9c424298c2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1da791fae7c8b802c8de0642f25025fe311155d4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074760"
---
# <a name="attributepermission-element-assl"></a>AttributePermission 元素 (ASSL)
  定義的權限的成員[角色](role-element-assl.md)元素中個別維度屬性所擁有[Cube](cube-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<AttributePermissions>  
   <AttributePermission>  
      <AttributeID>...</AttributeID>  
      <Description>...</Description>  
      <DefaultMember>...</DefaultMember>  
            <VisualTotals>...</VisualTotals>  
      <AllowedSet>...</AllowedSet>  
            <DeniedSet>...</DeniedSet>  
      <Annotations>...</Annotations>  
   </AttributePermission>  
</AttributePermissions>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|None|  
|預設值|None|  
|基數|0-n：出現一次以上的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[AttributePermissions](../collections/attributepermissions-element-assl.md)|  
|子元素|[AllowedSet](../properties/allowedset-element-assl.md)，[註解](../collections/annotations-element-assl.md)， [AttributeID](../properties/id-element-assl.md)， [DefaultMember](member-element-assl.md)， [DeniedSet](../properties/deniedset-element-assl.md)，[描述](../properties/description-element-assl.md)， [VisualTotals](../properties/visualtotals-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 在 「 分析管理物件 (AMO) 物件模型的對應元素是<xref:Microsoft.AnalysisServices.AttributePermission>。  
  
## <a name="see-also"></a>另請參閱  
 [CubeDimensionPermission 資料類型&#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [物件&#40;ASSL&#41;](objects-assl.md)  
  
  
