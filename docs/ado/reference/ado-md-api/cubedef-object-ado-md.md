---
description: CubeDef 物件 (ADO MD)
title: CubeDef 物件 (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CubeDef
helpviewer_keywords:
- CubeDef object [ADO MD]
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
author: rothja
ms.author: jroth
ms.openlocfilehash: cf8de68674ee1cc33f0ba16c9a0b3604418d0332
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441150"
---
# <a name="cubedef-object-ado-md"></a>CubeDef 物件 (ADO MD)
表示多維架構中的 cube，其中包含一組相關的維度。  
  
## <a name="remarks"></a>備註  
 使用 **CubeDef** 物件的集合和屬性，您可以執行下列動作：  
  
-   使用[Name](../../../ado/reference/ado-md-api/name-property-ado-md.md)屬性來識別**CubeDef** 。  
  
-   傳回字串，這個字串描述具有 [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) 屬性的 cube。  
  
-   傳回組成 cube 和 [維度](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) 集合的維度。  
  
-   使用標準的 ADO[屬性](../../../ado/reference/ado-api/properties-collection-ado.md)集合取得**CubeDef**的其他資訊。  
  
 **Properties**集合包含提供者提供的屬性。 下表列出可能可用的屬性。 實際的屬性清單可能會因提供者的執行而有所不同。 如需可用屬性的完整清單，請參閱提供者的檔。  
  
|名稱|描述|  
|----------|-----------------|  
|CatalogName|此 cube 所屬之目錄的名稱。|  
|CreatedOn|建立 cube 的日期和時間。|  
|CubeGUID|Cube GUID。|  
|CubeName|Cube 的名稱。|  
|CubeType|Cube 的類型。|  
|DataUpdatedBy|執行上次資料更新之人員的使用者識別碼。|  
|描述|Cube 的有意義描述。|  
|LastSchemaUpdate|上次架構更新的日期和時間。|  
|SchemaName|此 cube 所屬的架構名稱。|  
|SchemaUpdatedBy|執行最後一個架構更新之人員的使用者識別碼。|  
  
 本節包含下列主題。  
  
-   [屬性、方法和事件](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [CubeDef 範例 (VBScript) ](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [類別目錄物件 (ADO MD) ](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [CubeDefs 集合 (ADO MD) ](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [維度集合 (ADO MD) ](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Properties 集合 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
