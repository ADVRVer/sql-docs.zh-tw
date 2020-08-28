---
description: IsolationLevel 屬性
title: IsolationLevel 屬性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
author: rothja
ms.author: jroth
ms.openlocfilehash: 91945d36801005fb7f7c4dbcc9df5a464c6e4fa4
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990769"
---
# <a name="isolationlevel-property"></a>IsolationLevel 屬性
表示 [連接](./connection-object-ado.md) 物件的隔離層級。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回 [IsolationLevelEnum](./isolationlevelenum.md) 值。 預設值為 **adXactReadCommitted**。  
  
## <a name="remarks"></a>備註  
 您可以使用 **IsolationLevel** 屬性來設定 **連接** 物件的隔離等級。 除非您下一次呼叫 [BeginTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md) 方法，否則設定不會生效。 如果您要求的隔離層級無法使用，則提供者可能會傳回下一個較高層級的隔離，而不會更新 **IsolationLevel** 屬性。  
  
 **IsolationLevel**屬性為 read/write。  
  
> [!NOTE]
>  **遠端資料服務使用量** 使用於用戶端 **連接** 物件時， **IsolationLevel** 屬性只能設定為 **adXactUnspecified**。 由於使用者在用戶端快取上使用已中斷連線的 **記錄集** 物件，因此可能會有多使用者的問題。 比方說，當兩個不同的使用者嘗試更新相同的記錄時，遠端資料服務只會讓更新記錄的使用者「獲勝」。 第二個使用者的更新要求會失敗，並出現錯誤。  
  
## <a name="applies-to"></a>套用至  
 [Connection 物件 (ADO)](./connection-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [IsolationLevel 和 Mode 屬性範例 (VB) ](./isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel 和 Mode 屬性範例 (VC + +) ](./isolationlevel-and-mode-properties-example-vc.md)