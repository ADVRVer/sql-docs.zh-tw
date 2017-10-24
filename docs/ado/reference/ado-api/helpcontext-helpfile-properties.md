---
title: "HelpContext、 HelpFile 屬性 |Microsoft 文件"
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
- Error::GetHelpContext
- Error::GetHelpFile
- Error::get_HelpFile
- Error::get_HelpContext
- Error::HelpContext
- Error::HelpFile
helpviewer_keywords:
- HelpContext property [ADO]
- HelpFile property [ADO]
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0474b7b80eebb70e181df58d22f293c388a628bb
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="helpcontext-helpfile-properties"></a>HelpContext，HelpFile 屬性
表示說明檔和相關聯的主題[錯誤](../../../ado/reference/ado-api/error-object.md)物件。  
  
## <a name="return-values"></a>傳回值  
  
-   **文字串**傳回的內容識別碼，做為**長**的說明檔主題的值。  
  
-   **HelpFile**傳回**字串**評估為完全解決的說明檔路徑的值。  
  
## <a name="remarks"></a>備註  
 如果說明檔中指定了**HelpFile**屬性， **HelpContext**屬性用來自動顯示 [說明] 主題，它會識別。 如果有不可用的任何相關的說明主題， **HelpContext**屬性會傳回零和**HelpFile**屬性會傳回零長度字串 ("")。  
  
## <a name="applies-to"></a>適用於  
 [Error 物件](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>另請參閱  
 [描述、 HelpContext、 說明檔案、 NativeError、 數字、 來源和 SQLState 屬性範例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [描述、 HelpContext、 說明檔案、 NativeError、 數字、 來源和 SQLState 屬性範例 （VC + +）](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description 屬性](../../../ado/reference/ado-api/description-property.md)   
 [Number 屬性 (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [來源屬性 （ADO 錯誤）](../../../ado/reference/ado-api/source-property-ado-error.md)

