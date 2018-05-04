---
title: Requery 方法 |Microsoft 文件
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords:
- Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae5c1d47d36f9e7238d97761fa33fa14baf9151d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="requery-method"></a>Requery 方法
更新中的資料[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)重新執行查詢所依據之物件的物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>參數  
 *選項。*  
 選擇性。 位元遮罩，其中包含[的執行方式](../../../ado/reference/ado-api/executeoptionenum.md)和[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)值會影響這項作業。  
  
> [!NOTE]
>  如果*選項*設**adAsyncExecute**，這項作業會以非同步方式執行和[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)結束時，它時，就會發出事件。 **ExecuteOpenEnum**值**adExecuteNoRecords**或**adExecuteStream**不應與**Requery**。  
  
## <a name="remarks"></a>備註  
 使用**Requery**方法，以重新整理的整個內容**資料錄集**重新發出原始命令，並擷取資料的第二次資料來源的物件。 呼叫這個方法相當於呼叫[關閉](../../../ado/reference/ado-api/close-method-ado.md)和[開啟](../../../ado/reference/ado-api/open-method-ado-recordset.md)連續的方法。 如果您正在編輯目前的記錄，或加入新的記錄，就會發生錯誤。  
  
 雖然**資料錄集**物件是否開啟，定義資料指標的本質的屬性 ([CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)， [LockType](../../../ado/reference/ado-api/locktype-property-ado.md)， [MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)依此類推) 處於唯讀狀態。 因此， **Requery**方法只重新整理目前的資料指標。 若要變更任何資料指標屬性並檢視結果，您必須使用[關閉](../../../ado/reference/ado-api/close-method-ado.md)方法，讓內容會再次變成讀取/寫入。 接著，您可以變更屬性設定和呼叫[開啟](../../../ado/reference/ado-api/open-method-ado-recordset.md)方法，以重新開啟資料指標。  
  
## <a name="applies-to"></a>適用於  
 [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [執行，請重新查詢，並清除方法範例 (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [執行，請重新查詢，並清除方法範例 (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [執行，請重新查詢，並清除方法範例 （VC + +）](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandText 屬性 (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)
