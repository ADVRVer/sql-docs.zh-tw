---
title: 來源屬性 (ADO Error) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 89a4597cc846db1bb3bb2fac0a79ec8c2090d9d3
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711143"
---
# <a name="source-property-ado-error"></a>Source 屬性 (ADO Error)
表示物件或最初產生錯誤的應用程式的名稱。  
  
## <a name="return-value"></a>傳回值  
 傳回**字串**值，指出物件或應用程式的名稱。  
  
## <a name="remarks"></a>備註  
 使用**來源**屬性上的[錯誤](../../../ado/reference/ado-api/error-object.md)物件來判斷最初產生錯誤的應用程式之物件的名稱。 這可能是物件的類別名稱或程式設計識別碼。 在 ADO 中的錯誤，此屬性值會是**ADODB。** _ObjectName_，其中*ObjectName*觸發錯誤的物件名稱。 ADOX 和 ADO MD，此值會是**ADOX。** _ObjectName_並**ADOMD。** _ObjectName_分別。  
  
 根據的錯誤說明文件**來源**，[數目](../../../ado/reference/ado-api/number-property-ado.md)，並[描述](../../../ado/reference/ado-api/description-property.md)屬性**錯誤**物件時，您可以撰寫程式碼會適當地處理錯誤。  
  
 **來源**屬性是唯讀**錯誤**物件。  
  
## <a name="applies-to"></a>適用於  
 [Error 物件](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>另請參閱  
 [描述、 HelpContext、 HelpFile、 NativeError、 數目、 來源和 SQLState 屬性範例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [描述、 HelpContext、 HelpFile、 NativeError、 數目、 來源和 SQLState 屬性範例 （VC + +）](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description 屬性](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext、 HelpFile 屬性](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number 屬性 (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [來源屬性 （ADO 記錄）](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Source 屬性 (ADO Recordset)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
