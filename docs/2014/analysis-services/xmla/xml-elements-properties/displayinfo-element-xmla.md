---
title: DisplayInfo 元素 (XMLA) |Microsoft Docs
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
- DisplayInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.displayinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#DisplayInfo
- urn:schemas-microsoft-com:xml-analysis#DisplayInfo
helpviewer_keywords:
- DisplayInfo element
ms.assetid: 059ce038-38de-4c7d-a72f-4f919cfc7c4a
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 697678969f3e1f59f3a9d379d791bf285f0513be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321154"
---
# <a name="displayinfo-element-xmla"></a>DisplayInfo 元素 (XMLA)
  包含父代的顯示資訊[HierarchyInfo](hierarchyinfo-element-xmla.md)或是[成員](member-element-xmla.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <DisplayInfo>...</DisplayInfo>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|unsignedInt|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[HierarchyInfo](hierarchyinfo-element-xmla.md)，[成員](member-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 `DisplayInfo` 元素包含各種資訊項目，可協助用戶端應用程式轉譯 `HierarchyInfo` 或 `Member` 父元素。 此值相當於針對 OLE DB for OLAP 規格中軸資料列集定義的 DISPLAY_INFO 屬性。  
  
## <a name="see-also"></a>另請參閱  
 [屬性&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
