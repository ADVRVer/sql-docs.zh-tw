---
title: "Append 方法 （ADOX 程序） |Microsoft 文件"
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
f1_keywords:
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 679f7691a8f93026ce1f6a68ea232d01818e6dc9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="append-method-adox-procedures"></a>Append 方法 （ADOX 程序）
將新[程序](../../../ado/reference/adox-api/procedure-object-adox.md)物件[程序](../../../ado/reference/adox-api/procedures-collection-adox.md)集合。  
  
## <a name="syntax"></a>語法  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>參數  
 *名稱*  
 A**字串**值，指定要建立並附加的程序名稱。  
  
 *Command*  
 ADO[命令](../../../ado/reference/ado-api/command-object-ado.md)物件，表示要建立並附加的程序。  
  
## <a name="remarks"></a>備註  
 建立新的程序中指定的屬性名稱與資料來源中**命令**物件。  
  
 如果使用者指定的命令文字表示的檢視，而不是程序，則行為是取決於所使用的提供者。 **附加**如果提供者不支援持續性命令將會失敗。  
  
> [!NOTE]
>  使用 Microsoft Jet OLE DB 提供者時**程序**集合**附加**方法將允許您指定**檢視**而不是**程序**中*命令*參數。 **檢視**會加入至資料來源，就會加入至**程序**集合。 之後**附加**，如果**程序**和**檢視**重新整理集合時，**檢視**將不再處於**程序**集合會出現在**檢視**集合。  
  
## <a name="applies-to"></a>適用於  
 [程序集合 (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>另請參閱  
 [程序附加方法範例 (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append 方法 （ADOX 資料行）](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append 方法 （ADOX 群組）](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append 方法 （ADOX 索引）](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append 方法 （ADOX 索引鍵）](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append 方法 （ADOX 資料表）](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append 方法 （ADOX 使用者）](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append 方法 （ADOX 檢視）](../../../ado/reference/adox-api/append-method-adox-views.md)

