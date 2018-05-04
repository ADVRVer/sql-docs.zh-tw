---
title: 成員集合 (ADO MD) |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Members
- Members
- Position::Members
helpviewer_keywords:
- Members collection [ADO MD]
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18a3fac9cff0a41c9d1e7dc820d68ae77c294d4a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="members-collection-ado-md"></a>成員集合 (ADO MD)
包含[成員](../../../ado/reference/ado-md-api/member-object-ado-md.md)物件層級或沿座標軸的位置。  
  
## <a name="remarks"></a>備註  
 A**成員**集合用來包含下列類型的成員：  
  
-   構成 cube 中的層級的成員。 包含在**成員**集合[層級](../../../ado/reference/ado-md-api/level-object-ado-md.md)物件。 例如，使用從範例[概觀的多維度結構描述和資料](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)，國家 （地區） 層級的四個成員是加拿大、 美國、 英國及德國。  
  
-   在階層中的特定成員子系的成員。 這些成員會傳回由[子系](../../../ado/reference/ado-md-api/children-property-ado-md.md)屬性之父代**成員**物件。 例如，一次使用相同的範例，兩個的子系 Canada 成員是加拿大東部和加拿大西部。  
  
-   定義座標軸上的特定位置的成員[資料格集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)。 使用 從資料格集[使用多維度資料](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)為例，x 軸上的第一個位置的兩個成員都情人和西雅圖。 包含在這些成員**成員**集合[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)物件。  
  
 **成員**是標準的 ADO 集合。 具有屬性和方法的集合，您可以執行下列作業：  
  
-   取得集合中的物件數目[計數](../../../ado/reference/ado-api/count-property-ado.md)屬性。  
  
-   傳回物件集合中具有預設[項目](../../../ado/reference/ado-api/item-property-ado.md)屬性。  
  
-   更新的提供者從集合中的物件[重新整理](../../../ado/reference/ado-api/refresh-method-ado.md)方法。  
  
 本章節包含下列主題。  
  
-   [屬性、 方法和事件](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [成員範例 (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Member 物件 (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
