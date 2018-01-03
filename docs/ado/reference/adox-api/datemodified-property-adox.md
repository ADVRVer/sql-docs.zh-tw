---
title: "DateModified 屬性 (ADOX) |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords: DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e334d9c316b8655b475f24554e3e3f6843bd884
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="datemodified-property-adox"></a>DateModified 屬性 (ADOX)
指出上次修改物件的日期。  
  
## <a name="return-values"></a>傳回值  
 傳回**Variant**值，指定 修改日期。 此值為 null 如果**DateModified**提供者不支援。  
  
## <a name="remarks"></a>備註  
 **DateModified**屬性為 null，新附加的物件。 附加新之後[檢視](../../../ado/reference/adox-api/view-object-adox.md)或[程序](../../../ado/reference/adox-api/procedure-object-adox.md)，您必須呼叫[重新整理](../../../ado/reference/ado-api/refresh-method-ado.md)方法[檢視](../../../ado/reference/adox-api/views-collection-adox.md)或[程序](../../../ado/reference/adox-api/procedures-collection-adox.md)要取得的值集合**DateModified**屬性。  
  
## <a name="applies-to"></a>適用於  
  
||||  
|-|-|-|  
|[Procedure 物件 (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table 物件 (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View 物件 (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>請參閱  
 [DateCreated 和 DateModified 屬性範例 (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated 屬性 (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
