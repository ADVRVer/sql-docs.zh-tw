---
title: GetObjectOwner 方法 (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b2c967ac293ed59fde6494e12c2afc2c5b6de90
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687206"
---
# <a name="getobjectowner-method-adox"></a>GetObjectOwner 方法 (ADOX)
傳回物件的擁有者[目錄](../../../ado/reference/adox-api/catalog-object-adox.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>傳回值  
 傳回**字串**值，指定[名稱](../../../ado/reference/adox-api/name-property-adox.md)的[使用者](../../../ado/reference/adox-api/user-object-adox.md)或是[群組](../../../ado/reference/adox-api/group-object-adox.md)擁有的物件。  
  
#### <a name="parameters"></a>參數  
 *ObjectName*  
 A**字串**值，指定要傳回其擁有者的物件名稱。  
  
 *ObjectType*  
 A**長**可以是其中一值的[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)常數，指定要取得擁有者的物件型別。  
  
 *ObjectTypeId*  
 選擇性。 A **Variant** OLE DB 規格所定義的值，不指定提供者物件類型的 GUID。 如果此參數，則需要*ObjectType*設為**adPermObjProviderSpecific**，否則不會使用它。  
  
## <a name="remarks"></a>備註  
 如果提供者不支援傳回的物件擁有者，就會發生錯誤。  
  
## <a name="applies-to"></a>適用於  
 [Catalog 物件 (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>另請參閱  
 [GetObjectOwner 和 SetObjectOwner 方法範例 (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [SetObjectOwner 方法](../../../ado/reference/adox-api/setobjectowner-method.md)
