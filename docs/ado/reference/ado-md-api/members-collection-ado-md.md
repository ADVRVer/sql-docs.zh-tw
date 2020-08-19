---
description: Members 集合 (ADO MD)
title: 成員集合 (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Members
- Members
- Position::Members
helpviewer_keywords:
- Members collection [ADO MD]
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
author: rothja
ms.author: jroth
ms.openlocfilehash: a39565e51270684a5514d499c658f950fe473a1e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440870"
---
# <a name="members-collection-ado-md"></a>Members 集合 (ADO MD)
包含來自層級的 [成員](../../../ado/reference/ado-md-api/member-object-ado-md.md) 物件，或是沿著軸的位置。  
  
## <a name="remarks"></a>備註  
 **成員**集合是用來包含下列類型的成員：  
  
-   組成 cube 中層級的成員。 這些會包含在[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)物件的**Members**集合中。 例如，使用多 [維度架構和資料的總覽](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)範例，國家（地區）層級的四個成員為加拿大、USA、UK 和德國。  
  
-   隸屬于階層內特定成員之子系的成員。 父**成員**物件的[子](../../../ado/reference/ado-md-api/children-property-ado-md.md)屬性會傳回這些成員。 例如，使用相同的範例，加拿大成員的兩個子系是加拿大東部和加拿大西部。  
  
-   成員，定義沿著 [儲存格](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)軸的特定位置。 使用 [資料](../../../ado/guide/multidimensional/working-with-multidimensional-data.md) 格集做為範例，X 軸上第一個位置的兩個成員是情人節和西雅圖。 [位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)物件的**成員**集合包含這些成員。  
  
 **成員** 是標準的 ADO 集合。 使用集合的屬性和方法，您可以執行下列動作：  
  
-   使用 [Count](../../../ado/reference/ado-api/count-property-ado.md) 屬性取得集合中的物件數目。  
  
-   從集合中傳回具有預設 [專案](../../../ado/reference/ado-api/item-property-ado.md) 屬性的物件。  
  
-   使用 [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) 方法，從提供者更新集合中的物件。  
  
 本節包含下列主題。  
  
-   [屬性、方法和事件](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [ (VBScript) 的成員範例 ](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Member 物件 (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
