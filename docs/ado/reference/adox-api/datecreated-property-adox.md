---
title: "DateCreated 屬性 (ADOX) |Microsoft 文件"
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
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0403fbd8d7136f008a2ec3bd2ee3071f40ce2cf2
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="datecreated-property-adox"></a>DateCreated 屬性 (ADOX)
指出物件已建立的日期。  
  
## <a name="return-values"></a>傳回值  
 傳回**Variant**值，指定建立的日期。 此值為 null 如果**DateCreated**提供者不支援。  
  
## <a name="remarks"></a>備註  
 **DateCreated**屬性為 null，新附加的物件。 附加新之後[檢視](../../../ado/reference/adox-api/view-object-adox.md)或[程序](../../../ado/reference/adox-api/procedure-object-adox.md)，您必須呼叫[重新整理](../../../ado/reference/ado-api/refresh-method-ado.md)方法[檢視](../../../ado/reference/adox-api/views-collection-adox.md)或[程序](../../../ado/reference/adox-api/procedures-collection-adox.md)要取得的值集合**DateCreated**屬性。  
  
## <a name="applies-to"></a>適用於  
  
||||  
|-|-|-|  
|[程序物件 (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table 物件 (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[檢視物件 (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>另請參閱  
 [DateCreated 和 DateModified 屬性範例 (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateModified 屬性 (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)

