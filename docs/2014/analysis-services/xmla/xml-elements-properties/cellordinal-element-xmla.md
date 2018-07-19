---
title: CellOrdinal 元素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CellOrdinal Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cellordinal
- urn:schemas-microsoft-com:xml-analysis#CellOrdinal
- http://schemas.microsoft.com/analysisservices/2003/engine#CellOrdinal
helpviewer_keywords:
- CellOrdinal element
ms.assetid: 1808c498-e3b4-4e5c-9e22-7f8662d32874
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0e8e0413afb58ae448a053e9eab20d77a1b36096
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245368"
---
# <a name="cellordinal-element-xmla"></a>CellOrdinal 元素 (XMLA)
  包含更新的儲存格的 cube 中的序數位置[UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)命令。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Cell>  
   ...  
   <CellOrdinal>...</CellOrdinal>  
   ...  
</Cell>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|長整數|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[資料格](cell-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 `CellOrdinal` 元素會識別要由 `UpdateCells` 命令更新的資料格。  
  
 如需更新資料格的詳細資訊，請參閱[更新資料格 &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md)。  
  
## <a name="see-also"></a>另請參閱  
 [值項目&#40;XMLA&#41;](value-element-xmla.md)   
 [UpdateCells 元素&#40;XMLA&#41;](../xml-elements-commands/updatecells-element-xmla.md)   
 [屬性&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
