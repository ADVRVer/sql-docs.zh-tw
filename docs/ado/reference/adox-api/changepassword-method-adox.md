---
description: ChangePassword 方法 (ADOX)
title: ChangePassword 方法 (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
author: rothja
ms.author: jroth
ms.openlocfilehash: e51037f9838e9aef279351c822e6c35ffb25f0fb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985199"
---
# <a name="changepassword-method-adox"></a>ChangePassword 方法 (ADOX)
變更 [使用者](./user-object-adox.md) 帳戶的密碼。  
  
## <a name="syntax"></a>語法  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>參數  
 *OldPassword*  
 指定使用者現有密碼的 **字串** 值。 如果使用者目前沒有密碼，請針對 *OldPassword*使用空字串 ( "" ) 。  
  
 *NewPassword*  
 指定新密碼的 **字串** 值。  
  
## <a name="remarks"></a>備註  
 基於安全性理由，除了新密碼之外，還必須指定舊密碼。  
  
 如果提供者不支援管理受信任的屬性，就會發生錯誤。  
  
## <a name="applies-to"></a>套用至  
 [User 物件 (ADOX)](./user-object-adox.md)  
  
## <a name="see-also"></a>另請參閱  
 [Groups 和 Users Append、ChangePassword 方法範例 (VB)](./groups-and-users-append-changepassword-methods-example-vb.md)