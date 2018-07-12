---
title: DeleteWithDescendants 元素 (XMLA) |Microsoft Docs
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
- DeleteWithDescendants Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DeleteWithDescendants
- microsoft.xml.analysis.deletewithdescendants
- urn:schemas-microsoft-com:xml-analysis#DeleteWithDescendants
helpviewer_keywords:
- DeleteWithDescendants element
ms.assetid: adfc9437-aaa7-4364-bcdb-128fcc9a410d
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9aa39e4091c0d2fcde431a9f859c7a9b7a0e6e34
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155249"
---
# <a name="deletewithdescendants-element-xmla"></a>DeleteWithDescendants 元素 (XMLA)
  指出是否屬性成員的下階也會刪除父代[卸除](../xml-elements-commands/drop-element-xmla.md)命令。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Drop>  
   ...  
   <DeleteWithDescendants>...</DeleteWithDescendants>  
   ...  
</Drop>  
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
|父元素|[卸除](../xml-elements-commands/drop-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 `DeleteWithDescendants`元素會決定是否`Drop`命令應刪除所識別的屬性成員[其中](where-element-xmla.md)項目，但是，這些屬性成員的子系會一併卸除。  
  
> [!NOTE]  
>  這個元素只會套用至父子式階層中的屬性成員。  
  
 如需刪除和更新屬性成員的詳細資訊，請參閱[插入、更新和卸除成員 &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md)。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
