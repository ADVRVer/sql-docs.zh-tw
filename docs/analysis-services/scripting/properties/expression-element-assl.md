---
title: "Expression 元素 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Expression Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Expression
helpviewer_keywords:
- Expression element
ms.assetid: a9491b21-5279-4531-b6a5-9e8022060dd8
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4b6a1ee790691a1c48b7bdea13c92acccb53bbde
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="expression-element-assl"></a>Expression 元素 (ASSL)
  包含定義父元素內容的多維度運算式 (MDX) 運算式。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)， [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 如**CellPermission**項目，**運算式**元素包含邏輯 MDX 運算式來識別適用於所指定的權限的資料格[存取](../../../analysis-services/scripting/properties/access-element-assl.md)項目**CellPermission**項目。 如果值**運算式**元素**CellPermission**元素是空的**CellPermission**項目會被忽略。  
  
 如**StandardAction**項目，**運算式**元素包含 MDX 運算式，表示動作的內容。 如果值**運算式**元素**StandardAction**元素是空的**StandardAction**項目會被忽略。  
  
 在「分析管理物件」(AMO) 物件模型中對應至父系的元素是 <xref:Microsoft.AnalysisServices.CellPermission> 和 <xref:Microsoft.AnalysisServices.StandardAction>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

