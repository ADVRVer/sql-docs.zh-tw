---
title: "群組物件 (ADOX) |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 89733cc0f4533320e07d701f6645e64dac224fe3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="group-object-adox"></a>群組物件 (ADOX)
代表有受保護的資料庫內的存取權限的群組帳戶。  
  
## <a name="remarks"></a>備註  
 [群組](../../../ado/reference/adox-api/groups-collection-adox.md)集合[目錄](../../../ado/reference/adox-api/catalog-object-adox.md)代表所有類別目錄的群組帳戶。 **群組**集合[使用者](../../../ado/reference/adox-api/user-object-adox.md)代表只有使用者所隸屬的群組。  
  
 包含屬性、 集合，而且方法**群組**物件，您可以：  
  
-   識別具有群組[名稱](../../../ado/reference/adox-api/name-property-adox.md)屬性。  
  
-   判斷是否群組具有讀取、 寫入或刪除權限與[GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md)和[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)方法。  
  
-   存取具有成員資格的群組中的使用者帳戶[使用者](../../../ado/reference/adox-api/users-collection-adox.md)集合。  
  
-   存取提供者特有的屬性，與[屬性](../../../ado/reference/ado-api/properties-collection-ado.md)集合。  
  
 本章節包含下列主題。  
  
-   [Group 物件屬性、方法和事件](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [群組集合 (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Users 集合 (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
