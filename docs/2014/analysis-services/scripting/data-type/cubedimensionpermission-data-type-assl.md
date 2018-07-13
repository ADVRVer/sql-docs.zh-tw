---
title: CubeDimensionPermission 資料類型 (ASSL) |Microsoft Docs
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
- CubeDimensionPermission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeDimensionPermission
helpviewer_keywords:
- CubeDimensionPermission data type
ms.assetid: d9d39859-5f33-48bc-a402-0071755918de
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17bd5df3cd2dad116384d28e1f427d14a86b6b72
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180825"
---
# <a name="cubedimensionpermission-data-type-assl"></a>CubeDimensionPermission 資料類型 (ASSL)
  定義代表在 Cube 中特定維度上單一角色之權限的基本資料類型。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CubeDimensionPermission>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Description>...</Description>  
   <Read>...</Read>  
   <Write>...</Write>  
   <AttributePermissions>...</AttributePermissions>  
   <Annotations>...</Annotations>  
</CubeDimensionPermission>  
```  
  
## <a name="data-type-characteristics"></a>資料類型特性  
  
|特性|描述|  
|--------------------|-----------------|  
|基底資料類型|無|  
|衍生資料類型|無|  
  
## <a name="data-type-relationships"></a>資料類型關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|無|  
|子元素|[註釋](../collections/annotations-element-assl.md)， [AttributePermissions](../collections/attributepermissions-element-assl.md)， [CubeDimensionID](../properties/id-element-assl.md)，[描述](../properties/description-element-assl.md)，[讀取](../properties/read-element-assl.md)， [寫入](../properties/write-element-assl.md)|  
|衍生的元素|[DimensionPermission](../objects/dimensionpermission-element-assl.md) ([DimensionPermissions](../collections/dimensionpermissions-element-assl.md)的集合[維度](../objects/dimension-element-assl.md)或是[CubePermission](../objects/cubepermission-element-assl.md))|  
  
## <a name="remarks"></a>備註  
 在 「 分析管理物件 (AMO) 物件模型的對應元素是<xref:Microsoft.AnalysisServices.CubeDimensionPermission>。  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 指令碼語言 XML 資料類型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
