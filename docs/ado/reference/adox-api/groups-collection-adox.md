---
description: Groups 集合 (ADOX)
title: 群組集合 (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
author: rothja
ms.author: jroth
ms.openlocfilehash: 9624a30970e5a6f6a0186d2cb9e2390c98968d9e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984369"
---
# <a name="groups-collection-adox"></a>Groups 集合 (ADOX)
包含目錄或使用者的所有儲存的 [群組](./group-object-adox.md) 物件。  
  
## <a name="remarks"></a>備註  
 [目錄](./catalog-object-adox.md)的**Groups**集合代表所有目錄的群組帳戶。 [使用者](./user-object-adox.md)的**群組**集合只代表使用者所屬的群組。  
  
 **群組**集合的[APPEND](./append-method-adox-groups.md)方法對於 ADOX 而言是唯一的。 您可以：  
  
-   使用 **Append** 方法將新的安全性群組新增至集合。  
  
 其餘的屬性和方法是 ADO 集合的標準。 您可以：  
  
-   使用 [Item](../ado-api/item-property-ado.md) 屬性存取集合中的群組。  
  
-   傳回集合中包含 [Count](../ado-api/count-property-ado.md) 屬性的群組數目。  
  
-   使用 [Delete](./delete-method-adox-collections.md) 方法，從集合中移除群組。  
  
-   使用 [Refresh](../ado-api/refresh-method-ado.md) 方法更新集合中的物件，以反映目前的資料庫架構。  
  
> [!NOTE]
>  將**群組**物件附加至**使用者**物件的**群組**集合之前，**類別目錄****的群組集合中**必須已經[有同名的](./name-property-adox.md)**群組**物件。  
  
 本節包含下列主題。  
  
-   [Groups 集合屬性、方法和事件](./groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [ (ADOX) 的目錄物件 ](./catalog-object-adox.md)   
 [Group 物件 (ADOX)](./group-object-adox.md)