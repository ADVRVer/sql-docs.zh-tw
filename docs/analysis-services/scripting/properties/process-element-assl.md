---
title: 處理元素 (ASSL) |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Process Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Process
helpviewer_keywords:
- Process element
ms.assetid: 4aa08718-be44-4781-92cf-7b32b20f862c
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b93a6a88a636d568c67877321d1254aaf20dc104
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="process-element-assl"></a>Process 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]決定使用者是否可以處理父元素的擁有者。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Permission> <-- or one of the other elements contained in the Element Relationships table -->  
   ...  
   <Process>...</Process>  
   ...  
</Permission>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|布林|  
|預設值|False|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)， [DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)， [DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)， [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)， [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)，[權限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 對應至父系的項目**程序**在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.CubePermission>， <xref:Microsoft.AnalysisServices.DatabasePermission>， <xref:Microsoft.AnalysisServices.DimensionPermission>， <xref:Microsoft.AnalysisServices.MiningModelPermission>， <xref:Microsoft.AnalysisServices.MiningStructurePermission>，和<xref:Microsoft.AnalysisServices.Permission>。  
  
## <a name="see-also"></a>請參閱  
 [Role 元素 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
