---
title: "Description 屬性 |Microsoft 文件"
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
- Error::Description
- Error::GetDescription
- Error::get_Description
helpviewer_keywords:
- Description property
ms.assetid: 4b5d6790-6c29-42aa-bf78-d9cfb8ad7965
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c0672a00ca0cd2bbf67bcb7fb2f66a2f8bd6a00b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="description-property"></a>Description 屬性
描述[錯誤](../../../ado/reference/ado-api/error-object.md)物件。  
  
## <a name="return-value"></a>傳回值  
 傳回**字串**值，包含錯誤的描述。  
  
## <a name="remarks"></a>備註  
 使用**描述**屬性，以取得錯誤的簡短描述。 顯示這個屬性，以提醒使用者，您無法或不想要處理錯誤。 此字串會來自 ADO 或提供者。  
  
 提供者會負責將傳遞至 ADO 的特定錯誤文字。 ADO 將[錯誤](../../../ado/reference/ado-api/error-object.md)物件**錯誤**集合每個提供者的錯誤或警告它接收。 列舉**錯誤**追蹤提供者傳遞錯誤的集合。  
  
## <a name="applies-to"></a>適用於  
 [Error 物件](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>另請參閱  
 [描述、 HelpContext、 說明檔案、 NativeError、 數字、 來源和 SQLState 屬性範例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [描述、 HelpContext、 說明檔案、 NativeError、 數字、 來源和 SQLState 屬性範例 （VC + +）](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [HelpContext，HelpFile 屬性](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number 屬性 (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source 屬性 (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
