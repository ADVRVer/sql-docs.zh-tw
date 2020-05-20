---
title: Name 屬性（ADO MD） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Name
- CubeDef::Name
- Member::Name
- Catalog::Name
- Dimension::Name
- Name
- Axis::Name
- Hierarchy::Name
helpviewer_keywords:
- Name property [ADO MD]
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
author: rothja
ms.author: jroth
ms.openlocfilehash: 370dc7900e5fe876ea1b1064b2621371c730f323
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765088"
---
# <a name="name-property-ado-md"></a>Name 屬性 (ADO MD)
指出物件的名稱。  
  
## <a name="return-values"></a>傳回值  
 傳回**字串**，而且是唯讀的。  
  
## <a name="remarks"></a>備註  
 您可以使用序數參考抓取物件的**Name**屬性，之後您就可以直接依名稱參考該物件。 例如，如果 `cdf.CubeDefs(0).Name` 產生 "Bobs-machine Video Store"，您可以參考此[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)作為 `cdf.CubeDefs("Bobs Video Store")` 。  
  
## <a name="applies-to"></a>套用至  
  
||||  
|-|-|-|  
|[Axis 物件 (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Catalog 物件 (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[CubeDef 物件 (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Dimension 物件 (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Hierarchy 物件 (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Level 物件 (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Member 物件 (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>另請參閱  
 [Catalog 範例（VB）](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Caption 屬性（ADO MD）](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Description 屬性（ADO MD）](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [UniqueName 屬性 (ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
