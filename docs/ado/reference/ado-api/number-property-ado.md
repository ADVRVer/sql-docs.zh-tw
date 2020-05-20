---
title: Number 屬性（ADO） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
author: rothja
ms.author: jroth
ms.openlocfilehash: 02663507e19bf57f46b45ab7a99a717aec844dc4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762359"
---
# <a name="number-property-ado"></a>Number 屬性 (ADO)
指出唯一識別[錯誤](../../../ado/reference/ado-api/error-object.md)物件的數位。  
  
## <a name="return-value"></a>傳回值  
 傳回可能對應至其中一個[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)常數的**Long**值。  
  
## <a name="remarks"></a>備註  
 使用**Number**屬性來判斷發生的錯誤。 屬性的值是對應于錯誤條件的唯一數位。  
  
 [Errors](../../../ado/reference/ado-api/errors-collection-ado.md)集合會以十六進位格式（例如，0x80004005）或長值（例如2147467259）傳回 HRESULT。 這些 Hresult 可以由基礎元件（例如 OLE DB 或甚至是 OLE 本身）引發。 如需這些數位的詳細資訊，請參閱 OLE DB 程式設計[人員參考](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)中的[錯誤（OLE DB）](https://msdn.microsoft.com/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) *。*  
  
## <a name="applies-to"></a>套用至  
 [Error 物件](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>另請參閱  
 [Description、HelpCoNtext、內容説明、NativeError、Number、Source 和 SQLState 屬性範例（VB）](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpCoNtext、內容説明、NativeError、Number、Source 和 SQLState 屬性範例（VC + +）](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description 屬性](../../../ado/reference/ado-api/description-property.md)   
 [HelpCoNtext，內容説明的屬性](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Source 屬性 (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
