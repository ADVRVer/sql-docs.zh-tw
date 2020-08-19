---
description: Level 物件 (ADO MD)
title: 層級物件 (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level
helpviewer_keywords:
- Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
author: rothja
ms.author: jroth
ms.openlocfilehash: cdfcf6cb1411ae4f9ece9b917b5ecb1b76718766
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440950"
---
# <a name="level-object-ado-md"></a>Level 物件 (ADO MD)
包含一組成員，其中每個成員在階層內都有相同的順位。  
  
## <a name="remarks"></a>備註  
 使用 **層級** 物件的集合和屬性，您可以執行下列動作：  
  
-   使用 [[名稱](../../../ado/reference/ado-md-api/name-property-ado-md.md)] 和 [ [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) ] 屬性來識別**層級**。  
  
-   傳回使用[Caption](../../../ado/reference/ado-md-api/caption-property-ado-md.md)屬性顯示**層級**時要使用的字串。  
  
-   傳回描述具有[Description](../../../ado/reference/ado-md-api/description-property-ado-md.md)屬性之**層級**的有意義字串。  
  
-   傳回組成具有[成員](../../../ado/reference/ado-md-api/members-collection-ado-md.md)集合之**層級**的[成員](../../../ado/reference/ado-md-api/member-object-ado-md.md)物件。  
  
-   從具有[Depth](../../../ado/reference/ado-md-api/depth-property-ado-md.md)屬性之**層級**的根目錄傳回層級數目。  
  
-   您可以使用標準 ADO [屬性](../../../ado/reference/ado-api/properties-collection-ado.md) 集合來取得 **層級** 物件的其他資訊。  
  
 **Properties**集合包含提供者提供的屬性。 下表列出可能可用的屬性。 實際的屬性清單可能會因提供者的執行而有所不同。 如需可用屬性的完整清單，請參閱提供者的檔。  
  
|名稱|描述|  
|----------|-----------------|  
|CatalogName|此 cube 所屬之目錄的名稱。|  
|CubeName|Cube 的名稱。|  
|描述|層級的有意義描述。|  
|DimensionUniqueName|[維度](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)的明確名稱。|  
|HierarchyUniqueName|階層的明確名稱。|  
|LevelCaption|與層級相關聯的標籤或標題。|  
|LevelCardinality|層級中的成員數目。|  
|LevelGUID|層級的 GUID。|  
|LevelName|層級的名稱。|  
|LevelNumber|階層的層級和根目錄之間的距離。|  
|LevelType|層級的類型。|  
|LevelUniqueName|層級的明確名稱。|  
|SchemaName|此 cube 所屬的架構名稱。|  
  
 本節包含下列主題。  
  
-   [屬性、方法和事件](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [CubeDef 範例 (VBScript) ](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [階層物件 (ADO MD) ](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [層級集合 (ADO MD) ](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [成員集合 (ADO MD) ](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties 集合 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
