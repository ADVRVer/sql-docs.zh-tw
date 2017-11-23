---
title: "Append 方法 （ADOX 使用者） |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Users::raw_Append
- Users::Append
helpviewer_keywords: Append method [ADOX]
ms.assetid: b80bc5d5-78ca-4f75-956b-2ac658029cc7
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1720503f6ff8de32b247fa4878bccb69c88d5c71
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="append-method-adox-users"></a>Append 方法 （ADOX 使用者）
將新[使用者](../../../ado/reference/adox-api/user-object-adox.md)物件[使用者](../../../ado/reference/adox-api/users-collection-adox.md)集合。  
  
## <a name="syntax"></a>語法  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>參數  
 *使用者*  
 A **Variant**值，包含**使用者**来附加物件或建立並附加到使用者的名稱。  
  
 *密碼*  
 選擇性。 A**字串**值，包含使用者的密碼。 *密碼*參數會對應至所指定的值[ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md)方法**使用者**物件。  
  
## <a name="remarks"></a>備註  
 **使用者**集合[目錄](../../../ado/reference/adox-api/catalog-object-adox.md)代表所有類別目錄的使用者。 **使用者**集合[群組](../../../ado/reference/adox-api/group-object-adox.md)代表具有特定群組中的成員資格的使用者。  
  
 如果提供者不支援建立的使用者，會發生錯誤。  
  
> [!NOTE]
>  附加之前**使用者**物件**使用者**集合**群組**物件**使用者**物件具有相同[名稱](../../../ado/reference/adox-api/name-property-adox.md)為附加至其中一個必須已存在於**使用者**集合**目錄**。  
  
## <a name="applies-to"></a>適用於  
 [Users 集合 (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
  
## <a name="see-also"></a>請參閱＜  
 [群組和使用者附加、 ChangePassword 方法範例 (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append 方法 （ADOX 資料行）](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append 方法 （ADOX 群組）](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append 方法 （ADOX 索引）](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append 方法 （ADOX 索引鍵）](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append 方法 （ADOX 程序）](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append 方法 （ADOX 資料表）](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append 方法 (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
