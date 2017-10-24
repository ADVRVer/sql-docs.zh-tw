---
title: "屬性物件 (ADOX) |Microsoft 文件"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fa319e0fa981b3346232e3d3848bfdfe843d9f31
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="property-object-adox"></a>屬性物件 (ADOX)
代表 ADOX 物件的特性。  
  
## <a name="remarks"></a>備註  
 ADOX 物件有兩種類型的屬性： 內建和動態。  
  
 內建屬性是任何新的物件，使用 MyObject.Property 語法立即使用這些屬性。 它們不會出現為物件的屬性物件[屬性集合](../../../ado/reference/ado-api/properties-collection-ado.md)，因此，雖然您可以變更其值，您無法修改它們的特性。  
  
 動態屬性由基礎資料提供者所定義，並且顯示在適當的 ADOX 物件的屬性集合。  動態屬性可以參考只能透過使用 MyObject.Properties(0) 或 MyObject.Properties("Name") 語法在集合中。  
  
 您無法刪除任何一種屬性。  
  
 屬性的動態物件具有自己的四個內建屬性：  
  
 [名稱](../../../ado/reference/ado-api/name-property-ado.md)屬性是一個字串，識別屬性。  
  
 [類型](../../../ado/reference/ado-api/type-property-ado.md)屬性是整數，指定屬性資料型別。  
  
 [值](../../../ado/reference/ado-api/value-property-ado.md)屬性是包含的屬性設定為 variant。 值為屬性物件的預設屬性。  
  
 [屬性](../../../ado/reference/ado-api/attributes-property-ado.md)屬性是長值，指出提供者特定屬性的特性。  
  
 本章節包含下列主題。  
  
-   [ADOX 屬性物件屬性、 方法和事件](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)

