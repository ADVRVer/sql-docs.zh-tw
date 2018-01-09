---
title: "格式元素 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Format Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Format
helpviewer_keywords: Format element
ms.assetid: 881ea707-52a7-46f7-ba16-ac2ec44eca22
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a21fcaf86fde97f199b88f3248cb53fd8e64d5e4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="format-element-assl"></a>Format 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]包含所需的格式[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 允許的值為**格式**項目是 Microsoft Office Excel 格式，以及字串*TrimRight*， *TrimLeft*， *TrimAll*，和*TrimNone*。 進行修剪， *TrimRight*是預設值。  
  
 這個元素的值限制為下表所列的其中一個字串。  
  
|ReplTest1|描述|  
|-----------|-----------------|  
|任何 Excel 格式字串|資料會根據指定的具名或自訂格式字串格式化。 您可以提供 Excel 支援的任何格式字串。|  
|*TrimAll*|從左邊和右邊修剪資料。|  
|*TrimLeft*|從左邊修剪資料。|  
|*TrimNone*|不修剪資料。|  
|*TrimRight*|從右邊修剪資料。|  
  
 對應目的父代的項目**格式**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.DataItem>。  
  
## <a name="see-also"></a>請參閱  
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
