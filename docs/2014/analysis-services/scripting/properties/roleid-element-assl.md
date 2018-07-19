---
title: RoleID 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- RoleID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RoleID
helpviewer_keywords:
- RoleID element
ms.assetid: 811e24c9-c732-41f9-bd5f-5c9e3503706a
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cff4cf8a86160f1f4cef93d4cd021ac917038a33
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285914"
---
# <a name="roleid-element-assl"></a>RoleID 元素 (ASSL)
  識別要定義權限的角色。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Permission> <!-- or one of the listed below in the Element Relationships table -->  
   ...  
   <RoleID>...</RoleID>  
   ...  
</Permission>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[CubePermission](../objects/cubepermission-element-assl.md)， [DatabasePermission](../objects/databasepermission-element-assl.md)， [DimensionPermission](../objects/dimensionpermission-element-assl.md)， [MiningModelPermission](../objects/miningmodelpermission-element-assl.md)， [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)，[權限](../data-type/permission-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 在「分析管理物件」(AMO) 物件模型中對應至 `RoleID` 父系的元素是 <xref:Microsoft.AnalysisServices.CubePermission>、<xref:Microsoft.AnalysisServices.DatabasePermission>、<xref:Microsoft.AnalysisServices.DimensionPermission>、<xref:Microsoft.AnalysisServices.MiningModelPermission>、<xref:Microsoft.AnalysisServices.MiningStructurePermission> 和 <xref:Microsoft.AnalysisServices.Permission>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
