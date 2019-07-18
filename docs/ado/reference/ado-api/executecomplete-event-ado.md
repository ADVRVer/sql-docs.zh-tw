---
title: ExecuteComplete 事件 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 62b78b608526ae0d6943a7416a21687fd1e51412
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918786"
---
# <a name="executecomplete-event-ado"></a>ExecuteComplete 事件 (ADO)
**ExecuteComplete**命令已完成執行之後，系統會呼叫事件。  
  
## <a name="syntax"></a>語法  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>參數  
 *RecordsAffected*  
 A**長**值，指出受到該命令的記錄數目。  
  
 *pError*  
 [錯誤](../../../ado/reference/ado-api/error-object.md)物件。 它說明如果發生錯誤的值**adStatus**是**adStatusErrorsOccurred**; 否則它不會設定。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)狀態值。 呼叫此事件時，此參數設為**adStatusOK**造成事件的作業已順利完成，還是要**adStatusErrorsOccurred**如果作業失敗。  
  
 這個事件會傳回之前，請將此參數設定為**adStatusUnwantedEvent**以避免後續的通知。  
  
 *pCommand*  
 [命令](../../../ado/reference/ado-api/command-object-ado.md)已執行的物件。 包含**命令**物件呼叫，即使**Connection.Execute**或是**Recordset.Open**而不需要明確建立**命令**在哪些情況下**命令**物件在內部 ADO 來建立。  
  
 *pRecordset*  
 A[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件執行命令的結果。 這**資料錄集**可能是空的。 您應該永遠不會終結從這個資料錄集物件，此事件處理常式內。 這樣會導致存取違規，當 ADO 嘗試存取不存在的物件。  
  
 *pConnection*  
 A[連線](../../../ado/reference/ado-api/connection-object-ado.md)物件。 作業已執行連接。  
  
## <a name="remarks"></a>備註  
 **ExecuteComplete**事件可能是由於**連線。** [執行](../../../ado/reference/ado-api/execute-method-ado-connection.md)，**命令。** [執行](../../../ado/reference/ado-api/execute-method-ado-command.md)，**資料錄集。** [開放](../../../ado/reference/ado-api/open-method-ado-recordset.md)，**資料錄集。** [Requery](../../../ado/reference/ado-api/requery-method.md)，或**資料錄集。** [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [ADO 事件模型範例 （VC + +）](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO 事件處理常式摘要](../../../ado/guide/data/ado-event-handler-summary.md)
