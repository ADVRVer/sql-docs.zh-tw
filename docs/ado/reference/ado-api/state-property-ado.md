---
title: State 屬性（ADO） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
author: rothja
ms.author: jroth
ms.openlocfilehash: f4fa19bf21764437d3713c434e288b3bb3a3d25d
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242568"
---
# <a name="state-property-ado"></a>State 屬性 (ADO)
指出物件的狀態為開啟或關閉時，所有適用的物件。 如果物件正在執行非同步方法，則會指出物件的目前狀態為 [正在連接]、[執行中] 或 [正在抓取]。  
  
## <a name="return-value"></a>傳回值  
 傳回可以是[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)值的**Long**值。 預設值為**adStateClosed**。  
  
## <a name="remarks"></a>備註  
 您可以隨時使用**State**屬性來判斷指定物件的目前狀態。  
  
 物件的**State**屬性可以有值的組合。 例如，如果語句正在執行，此屬性會有**adStateOpen**和**adStateExecuting**的組合值。  
  
 **State**屬性是唯讀的。  
  
## <a name="applies-to"></a>套用至  

:::row:::
    :::column:::
        [Command 物件 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
        [Connection 物件 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Record 物件 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
        [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
    :::column:::
        [Stream 物件 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>另請參閱  
 [ConnectionString、ConnectionTimeout 和 State 屬性範例（VB）](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、ConnectionTimeout 和 State 屬性範例（VC + +）](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
