---
description: LockType 屬性 (ADO)
title: " (ADO) 的 LockType 屬性 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::LockType
helpviewer_keywords:
- LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
author: rothja
ms.author: jroth
ms.openlocfilehash: 49fe91535b674bb5dbb6c4a75425cdcea1042fa8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443340"
---
# <a name="locktype-property-ado"></a>LockType 屬性 (ADO)
表示在編輯期間放置於記錄上的鎖定類型。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回 [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) 值。 預設值為 **adLockReadOnly**。  
  
## <a name="remarks"></a>備註  
 在開啟記錄集之前設定 **LockType** 屬性，以指定提供者在開啟 [記錄集](../../../ado/reference/ado-api/recordset-object-ado.md) 時應使用的鎖定類型。 讀取屬性，以傳回在開啟的 **記錄集** 物件上使用的鎖定類型。  
  
 提供者可能不支援所有鎖定類型。 如果提供者無法支援要求的 **LockType** 設定，則會替代另一種類型的鎖定。 若要判斷 **記錄集** 物件中可用的實際鎖定功能，請使用 [支援](../../../ado/reference/ado-api/supports-method.md) 方法搭配 **adUpdate** 和 **adUpdateBatch**。  
  
 如果[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)屬性設定為**adUseClient**，則不支援**adLockPessimistic**設定。 如果設定了不支援的值，則不會產生任何錯誤;將改用最接近的支援 **LockType** 。  
  
 當**記錄集**已關閉時， **LockType**屬性是讀取/寫入，而當記錄開啟時，則為唯讀屬性。  
  
> [!NOTE]
>  **遠端資料服務使用量** 在用戶端 **記錄集** 物件上使用時， **LockType** 屬性只能設定為 **adLockBatchOptimistic**。  
  
## <a name="applies-to"></a>套用至  
 [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [CursorType、LockType 和 EditMode 屬性範例 (VB) ](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType、LockType 和 EditMode 屬性範例 (VC + +) ](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [ (ADO) 的 CancelBatch 方法 ](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [UpdateBatch 方法](../../../ado/reference/ado-api/updatebatch-method.md)
