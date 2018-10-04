---
title: DimensionPermissions 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DimensionPermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionPermissions
helpviewer_keywords:
- DimensionPermissions element
ms.assetid: cb9fdfbf-2118-423b-ba02-fa36813dbea0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af96e23a71064cb1d68c292f4224ee76b8395588
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068728"
---
# <a name="dimensionpermissions-element-assl"></a>DimensionPermissions 元素 (ASSL)
  包含適用於權限的集合[維度](../objects/dimension-element-assl.md)項目或有[CubePermission](../objects/cubepermission-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Dimension> <!-- or CubePermission -->  
   ...  
   <DimensionPermissions>  
            <DimensionPermission>...</DimensionPermission> <!-- parent: Dimension -->  
      <!-- or -->  
      <DimensionPermission xsi:type="CubeDimensionPermission">...</DimensionPermission> <!-- parent: CubePermission -->  
      </DimensionPermissions>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|None|  
|預設值|None|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[CubePermission](../objects/cubepermission-element-assl.md)，[維度](../objects/dimension-element-assl.md)|  
|子元素|[DimensionPermission](../objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 若為 `CubePermission` 元素，這個集合中的 `DimensionPermission` 元素會覆寫明確參考之每個維度的 `DimensionPermissions` 集合中指定的權限。 如果這個集合沒有參考某個維度，`CubePermission` 元素就會繼承該維度之 `DimensionPermissions` 集合中指定的權限。  
  
 在 「 分析管理物件 (AMO) 物件模型的對應元素是<xref:Microsoft.AnalysisServices.DimensionPermissionCollection>。  
  
## <a name="see-also"></a>另請參閱  
 [集合&#40;ASSL&#41;](collections-assl.md)  
  
  
