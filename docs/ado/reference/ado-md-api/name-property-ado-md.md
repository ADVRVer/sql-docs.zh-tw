---
title: Name 屬性 (ADO MD) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c6c9ba7f2981fd4162f93f37e6ad0eb2cbae882
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756766"
---
# <a name="name-property-ado-md"></a>Name 屬性 (ADO MD)
表示物件的名稱。  
  
## <a name="return-values"></a>傳回值  
 傳回**字串**和處於唯讀狀態。  
  
## <a name="remarks"></a>備註  
 您可以擷取**名稱**由序數參考之後, 您可以對物件直接依名稱參考物件的屬性。 例如，如果`cdf.CubeDefs(0).Name`會產生 [Bobs 影片 Store]，您可以參考此[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)做為`cdf.CubeDefs("Bobs Video Store")`。  
  
## <a name="applies-to"></a>適用於  
  
||||  
|-|-|-|  
|[Axis 物件 (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Catalog 物件 (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[CubeDef 物件 (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Dimension 物件 (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Hierarchy 物件 (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Level 物件 (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Member 物件 (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>另請參閱  
 [Catalog 範例 (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Caption 屬性 (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Description 屬性 (ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [UniqueName 屬性 (ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
