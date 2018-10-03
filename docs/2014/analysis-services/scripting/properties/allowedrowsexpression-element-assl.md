---
title: AllowedRowsExpression 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: ec24b11d-d11e-4369-a619-7e41a3c46159
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a23acca8488d5fa747d29338240cf98e0f703ecc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057248"
---
# <a name="allowedrowsexpression-element-assl"></a>AllowedRowsExpression 元素 (ASSL)
  包含定義父元素內容之布林類型的資料分析運算式 (DAX)。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|None|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[CellPermission](../objects/cellpermission-element-assl.md)， [StandardAction](../data-type/action-data-type-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 針對`CellPermission`項目，`Expression`項目包含邏輯 MDX 運算式來識別適用於所指定的權限的資料格[存取](access-element-assl.md)項目`CellPermission`項目。 如果 `Expression` 元素之 `CellPermission` 元素的值是空白的，系統就會忽略 `CellPermission` 元素。  
  
 若為 `StandardAction` 元素，`Expression` 元素會包含代表動作內容的 MDX 運算式。 如果 `Expression` 元素之 `StandardAction` 元素的值是空白的，系統就會忽略 `StandardAction` 元素。  
  
 在「分析管理物件」(AMO) 物件模型中對應至父系的元素是 <xref:Microsoft.AnalysisServices.CellPermission> 和 <xref:Microsoft.AnalysisServices.StandardAction>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
