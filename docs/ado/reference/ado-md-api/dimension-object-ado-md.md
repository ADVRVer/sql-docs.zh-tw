---
title: 維度物件 (ADO MD) |Microsoft 文件
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Dimension
helpviewer_keywords:
- Dimension object [ADO MD]
ms.assetid: 66adbbd2-23a3-4c19-a91b-84c31309aa1b
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8019ecec9222e1e6bb67633d225e3859734dcb7b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="dimension-object-ado-md"></a>維度物件 (ADO MD)
代表其中一個多維度 cube，其中包含一或多個成員階層的維度。  
  
## <a name="remarks"></a>備註  
 集合與屬性**維度**物件，您可以執行下列：  
  
-   識別**維度**與[名稱](../../../ado/reference/ado-md-api/name-property-ado-md.md)和[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)屬性。  
  
-   傳回有意義的字串描述**維度**與[描述](../../../ado/reference/ado-md-api/description-property-ado-md.md)屬性。  
  
-   傳回[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)構成物件**維度**與[階層](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)集合。  
  
-   使用標準的 ADO[屬性](../../../ado/reference/ado-api/properties-collection-ado.md)集合，以取得其他資訊有關**維度**物件。  
  
 **屬性**集合包含提供者提供的屬性。 下表列出可供使用的屬性。 實際的屬性清單可能與不同的提供者實作而定。 請參閱您的提供者，如需更完整清單可用內容的文件。  
  
|名稱|Description|  
|----------|-----------------|  
|CatalogName|此 cube 所屬的目錄的名稱。|  
|CubeName|Cube 的名稱。|  
|DefaultHierarchy|預設階層的唯一名稱。|  
|Description|Cube 有意義的描述。|  
|DimensionCaption|標籤或標題與維度相關聯。|  
|DimensionCardinality|在維度中的成員數目。|  
|DimensionGUID|維度的 GUID。|  
|DimensionName|維度的名稱。|  
|DimensionOrdinal|維度的構成 cube 的維度群組之間的序號。|  
|DimensionType|維度類型。|  
|DimensionUniqueName|維度的模稜兩可的名稱。|  
|SchemaName|此 cube 所屬的結構描述名稱。|  
  
 本章節包含下列主題。  
  
-   [屬性、 方法和事件](../../../ado/reference/ado-md-api/dimension-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [CubeDef 範例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [CubeDef 物件 (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)   
 [維度集合 (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Hierarchies 集合 (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Properties 集合 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
