---
title: LockTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9dbc6e9e78fc08be2bba08d0fbeb897496a2058b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694940"
---
# <a name="locktypeenum"></a>LockTypeEnum
指定在編輯期間鎖定記錄的型別。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|表示開放式的批次更新。 批次更新模式的必要項。|  
|**adLockOptimistic**|3|表示開放式鎖定、 記錄。 提供者會使用開放式鎖定，鎖定資料錄，只有當您呼叫時，才[更新](../../../ado/reference/ado-api/update-method.md)方法。|  
|**adLockPessimistic**|2|表示封閉式鎖定，記錄。 提供者會執行什麼是為了確保成功編輯的記錄，通常藉由編輯之後，立即鎖定在資料來源的記錄。|  
|**adLockReadOnly**|1|表示唯讀的記錄。 您無法改變的資料。|  
|**adLockUnspecified**|-1|未指定鎖定的類型。 複製程式碼，會使用相同的鎖定類型，與原始建立複製。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>適用於  
  
|||  
|-|-|  
|[Clone 方法 (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[LockType 屬性 (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open 方法 (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[WillExecute 事件 (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
