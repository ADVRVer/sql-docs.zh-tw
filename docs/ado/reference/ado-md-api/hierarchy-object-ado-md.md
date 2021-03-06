---
description: Hierarchy 物件 (ADO MD)
title: 階層物件 (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
author: rothja
ms.author: jroth
ms.openlocfilehash: 60d779ec3ed3393417725c9f574a798e5efc0efd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986649"
---
# <a name="hierarchy-object-ado-md"></a>Hierarchy 物件 (ADO MD)
表示 [維度](./dimension-object-ado-md.md) 成員可以匯總或「匯總」的一種方式。 維度可以沿著一或多個階層進行匯總。  
  
## <a name="remarks"></a>備註  
 利用 **階層物件的** 集合和屬性，您可以執行下列動作：  
  
-   識別具有[Name](./name-property-ado-md.md)和[UniqueName](./uniquename-property-ado-md.md) **屬性的階層**。  
  
-   傳回描述具有[Description](./description-property-ado-md.md)屬性之階層**的有**意義字串。  
  
-   傳回組成階層和[層](./levels-collection-ado-md.md)級**集合的**[層級](./level-object-ado-md.md)物件。  
  
-   使用標準 ADO [屬性](../ado-api/properties-collection-ado.md) 集合來取得 **階層物件的** 其他資訊。  
  
 **Properties**集合包含提供者提供的屬性。 下表列出可能可用的屬性。 實際的屬性清單可能會因提供者的執行而有所不同。 如需可用屬性的完整清單，請參閱提供者的檔。  
  
|名稱|描述|  
|----------|-----------------|  
|AllMember|階層中匯總最高層級的成員。|  
|CatalogName|此 cube 所屬之目錄的名稱。|  
|CubeName|Cube 的名稱。|  
|DefaultMember|此階層之預設成員的唯一名稱。|  
|描述|階層的有意義描述。|  
|DimensionType|此階層所屬維度的類型。|  
|DimensionUniqueName|維度的明確名稱。|  
|HierarchyCaption|與階層關聯的標籤或標題。|  
|HierarchyCardinality|階層中的成員數目。|  
|HierarchyGUID|階層的 GUID。|  
|HierarchyName|階層架構名稱。|  
|HierarchyUniqueName|階層的明確名稱。|  
|SchemaName|此 cube 所屬的架構名稱。|  
  
 本節包含下列主題。  
  
-   [屬性、方法和事件](./hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [CubeDef 範例 (VBScript) ](./cubedef-example-vbscript.md)   
 [維度物件 (ADO MD) ](./dimension-object-ado-md.md)   
 [階層集合 (ADO MD) ](./hierarchies-collection-ado-md.md)   
 [層級集合 (ADO MD) ](./levels-collection-ado-md.md)   
 [Properties 集合 (ADO)](../ado-api/properties-collection-ado.md)