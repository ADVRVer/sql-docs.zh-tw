---
description: WillChangeRecord 和 RecordChangeComplete 事件 (ADO)
title: WillChangeRecord 和 RecordChangeComplete 事件 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- RecordChangeComplete
- Recordset::WillChangeRecord
- WillChangeRecord
- Recordset::RecordChangeComplete
helpviewer_keywords:
- WillChangeRecord event [ADO]
- recordchangecomplete event [ADO]
ms.assetid: cbc369fd-63af-4a7d-96ae-efa91b78ca69
author: rothja
ms.author: jroth
ms.openlocfilehash: 8f69b16392204722e4efd3dc91602a920316919d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776877"
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>WillChangeRecord 和 RecordChangeComplete 事件 (ADO)
**WillChangeRecord**事件會在記錄[集](./recordset-object-ado.md)變更中)  (資料列之前呼叫。 **RecordChangeComplete**事件會在一或多筆記錄變更之後呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>參數  
 *adReason*  
 [EventReasonEnum](./eventreasonenum.md)值，指定這個事件的原因。 其值可以是 **adRsnAddNew**、 **adRsnDelete**、 **adRsnUpdate**、 **adRsnUndoUpdate**、 **adRsnUndoAddNew**、 **adRsnUndoDelete**或 **adRsnFirstChange**。  
  
 *cRecords*  
 **Long**值，指出 (受影響) 變更的記錄數目。  
  
 *pError*  
 [Error](./error-object.md)物件。 描述 *adStatus* 的值為 **adStatusErrorsOccurred**時所發生的錯誤;否則未設定。  
  
 *adStatus*  
 [EventStatusEnum](./eventstatusenum.md)狀態值。  
  
 當呼叫 **WillChangeRecord** 時，如果造成事件的作業成功，這個參數會設定為 **adStatusOK** 。 如果此事件無法要求取消暫止的作業，則會設定為 **adStatusCantDeny** 。  
  
 當呼叫 **RecordChangeComplete** 時，如果造成事件的作業成功，這個參數會設定為 **adStatusOK** ，如果作業失敗，則會 **adStatusErrorsOccurred** 。  
  
 在 **WillChangeRecord** 傳回之前，請將此參數設定為 **adStatusCancel** ，以要求取消導致這個事件的作業，或將此參數設定為 **adStatusUnwantedEvent** ，以防止後續的通知。  
  
 在 **RecordChangeComplete** 傳回之前，請將此參數設定為 **adStatusUnwantedEvent** ，以防止後續的通知。  
  
 *pRecordset*  
 **記錄集**物件。 發生此事件的 **記錄集** 。  
  
## <a name="remarks"></a>備註  
 由於下列**記錄集**作業，資料列中的第一個變更欄位可能會發生**WillChangeRecord**或**RecordChangeComplete**事件： [Update](./update-method.md)、 [Delete](./delete-method-ado-recordset.md)、 [CancelUpdate](./cancelupdate-method-ado.md)、 [AddNew](./addnew-method-ado.md)、 [UpdateBatch](./updatebatch-method.md)和[CancelBatch](./cancelbatch-method-ado.md)。 **記錄集** [CursorType](./cursortype-property-ado.md)的值會決定造成事件發生的作業。  
  
 在**WillChangeRecord**事件期間，[**記錄集**[篩選](./filter-property.md)] 屬性設定為 [ **adFilterAffectedRecords**]。 您無法在處理事件時變更此屬性。  
  
 您必須針對每個可能的**adReason**值，將**adStatus**參數設定為**adStatusUnwantedEvent** ，以完全停止任何包含**adReason**參數之事件的事件通知。  
  
## <a name="see-also"></a>另請參閱  
 [ADO 事件模型範例 (VC + +) ](./ado-events-model-example-vc.md)   
 [ADO 事件處理常式摘要](../../guide/data/ado-event-handler-summary.md)