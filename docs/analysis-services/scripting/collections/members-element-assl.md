---
title: Members 元素 (ASSL) |Microsoft 文件
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4c6d3eb270566bc387b2e9ce8ff48aec3c6531b6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032239"
---
# <a name="members-element-assl"></a>Members 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  包含集合[成員](../../../analysis-services/scripting/objects/member-element-assl.md)父元素的元素。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Group> <!-- or Role --<  
   ...  
   <Members>  
      <Member>...</Member>  
   </Members>  
   ...  
</Group>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[群組](../../../analysis-services/scripting/objects/group-element-assl.md)，[角色](../../../analysis-services/scripting/objects/role-element-assl.md)|  
|子元素|[成員](../../../analysis-services/scripting/objects/member-element-assl.md)|  
  
## <a name="remarks"></a>備註  
 對應至父系的項目**成員**在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.Group>和<xref:Microsoft.AnalysisServices.Role>。  
  
## <a name="see-also"></a>另請參閱  
 [集合 & #40;ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
