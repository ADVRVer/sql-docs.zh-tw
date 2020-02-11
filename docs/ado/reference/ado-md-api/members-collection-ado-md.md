---
title: Members 集合（ADO MD） |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 79394abee5b12bb10f34a34e882d2ac0562722fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949436"
---
# <a name="members-collection-ado-md"></a>Members 集合 (ADO MD)
包含來自層級的[成員](../../../ado/reference/ado-md-api/member-object-ado-md.md)物件或沿著軸的位置。  
  
## <a name="remarks"></a>備註  
 **成員**集合是用來包含下列類型的成員：  
  
-   組成 cube 中之層級的成員。 這些會包含在[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)物件的**Members**集合中。 例如，從多[維度架構和資料的總覽](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)使用範例，國家/地區層級的四個成員是加拿大、美國、英國和德國。  
  
-   階層中特定成員之子系的成員。 父**成員**物件的[子](../../../ado/reference/ado-md-api/children-property-ado-md.md)系屬性會傳回這些成員。 例如，再次使用相同的範例，加拿大成員的兩個子系為加拿大東部和加拿大西部。  
  
-   成員，其會沿著[集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)軸的座標軸定義特定位置。 使用資料格集來[處理多維度資料](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)做為範例，X 軸上第一個位置的兩個成員是情人節和西雅圖。 [位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)物件的**members**集合包含這些成員。  
  
 **成員**是標準的 ADO 集合。 使用集合的屬性和方法，您可以執行下列動作：  
  
-   使用[Count](../../../ado/reference/ado-api/count-property-ado.md)屬性取得集合中的物件數目。  
  
-   使用預設[專案](../../../ado/reference/ado-api/item-property-ado.md)屬性，從集合中傳回物件。  
  
-   使用[Refresh](../../../ado/reference/ado-api/refresh-method-ado.md)方法，從提供者更新集合中的物件。  
  
 本章節包含下列主題。  
  
-   [屬性、方法和事件](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [Members 範例（VBScript）](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Member 物件 (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
