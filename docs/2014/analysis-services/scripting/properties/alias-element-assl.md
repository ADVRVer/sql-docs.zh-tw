---
title: Alias 元素 (ASSL) |Microsoft 文件
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
- Alias Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Alias
helpviewer_keywords:
- Alias element
ms.assetid: 674fdb06-e33c-4f35-bd6a-d9bbb13ececa
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6da42c2c6e01a261972ce5d8b64fe738cc4734d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36023420"
---
# <a name="alias-element-assl"></a>Alias 元素 (ASSL)
  定義的別名[帳戶](../objects/account-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Aliases>  
      <Alias>...</Alias>  
</Aliases>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|無|  
|基數|0-n：出現一次以上的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[別名](../collections/aliases-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 `Alias` 元素的值會當做 `Account` 父元素所定義之帳戶的替代名稱使用，而且可協助識別使用者介面中帳戶類型和彙總函式的組合。  
  
 在「分析管理物件」(AMO) 物件模型中對應至 `Aliases` 集合父系的元素是 <xref:Microsoft.AnalysisServices.Account>。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  