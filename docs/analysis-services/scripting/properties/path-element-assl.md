---
title: 路徑元素 (ASSL) |Microsoft 文件
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
- Path Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Path
helpviewer_keywords:
- Path element
ms.assetid: 0edc59ac-1671-4fe1-9b7c-6c1548df5c63
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2de45a3724f1fd69f3553a8c3e92c6afb81bd337
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="path-element-assl"></a>Path 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]包含所提供的執行個體的路徑， [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]，所使用之報表的[ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<ReportAction>  
   ...  
   <Path>...</Path>  
   ...  
</ReportAction>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|無|  
|基數|0-1：只出現一次的選擇性元素|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 對應目的父代的項目**路徑**在 「 分析管理物件 (AMO) 物件模型而言， <xref:Microsoft.AnalysisServices.ReportAction>。  
  
## <a name="see-also"></a>請參閱  
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
