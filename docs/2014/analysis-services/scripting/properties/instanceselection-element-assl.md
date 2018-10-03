---
title: InstanceSelection 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- InstanceSelection Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- InstanceSelection element
ms.assetid: 908a2da9-274c-40d2-87dc-4641cb8d77e6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 41587ee5acd29ca8038e188a3a3a5681bb7b91d0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131458"
---
# <a name="instanceselection-element-assl"></a>InstanceSelection 元素 (ASSL)
  提供一個提示給用戶端應用程式，以便根據清單中的預期項目數目來建議應該如何顯示項目清單。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <InstanceSelection>...</InstanceSelection>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|字串 (列舉)|  
|預設值|*無*|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子元素|None|  
  
## <a name="remarks"></a>備註  
 這個元素的值限制為下列其中一個字串：  
  
|值|描述|  
|-----------|-----------------|  
|*無*|不要顯示選擇清單。 允許使用者直接輸入值。|  
|*下拉式清單中*|項目數目夠小，足以顯示在下拉式清單中。|  
|*清單*|項目數目太大，無法顯示在下拉式清單中，但不需要篩選。|  
|*FilteredList*|項目數目夠大，因此使用者必須篩選要顯示的項目。|  
|*MandatoryFilter*|項目數目非常大，所以一定要經過篩選才能顯示。|  
  
 在「分析管理物件」(AMO) 物件模型中對應至 `InstanceSelection` 允許值的列舉是 <xref:Microsoft.AnalysisServices.InstanceSelection>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
