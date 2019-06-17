---
title: InfoMessage 事件 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: edc451ae2075a22c106f4e2395836e7d508a7808
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694782"
---
# <a name="infomessage-event-ado"></a>InfoMessage 事件 (ADO)
**InfoMessage**期間發生警告時，會呼叫事件**ConnectionEvent**作業。  
  
## <a name="syntax"></a>語法  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>參數  
 *pError*  
 [錯誤](../../../ado/reference/ado-api/error-object.md)物件。 這個參數會包含任何傳回的錯誤。 如果傳回多個錯誤，列舉**錯誤**以找出它們的集合。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)狀態值。 發生警告時， *adStatus*設為**adStatusOK**並*pError*包含警告。  
  
 這個事件會傳回之前，請將此參數設定為**adStatusUnwantedEvent**以避免後續的通知。  
  
 *pConnection*  
 A[連線](../../../ado/reference/ado-api/connection-object-ado.md)物件。 警告發生的連線。 例如，開啟時可能會發生警告**連接**物件或執行[命令](../../../ado/reference/ado-api/command-object-ado.md)上**連接**。  
  
## <a name="see-also"></a>另請參閱  
 [ADO 事件模型範例 （VC + +）](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO 事件處理常式摘要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Connection 物件 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
