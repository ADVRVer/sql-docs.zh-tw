---
title: EventReasonEnum | Microsoft Docs
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- EventReasonEnum
helpviewer_keywords:
- EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a49c3aac3b2f37421df9a68ae01b16770c696993
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="eventreasonenum"></a>EventReasonEnum
指定造成事件發生的原因。  
  
|常數|Value|Description|  
|--------------|-----------|-----------------|  
|**adRsnAddNew**|1|作業會加入新的記錄。|  
|**adRsnClose**|9|關閉作業**資料錄集**。|  
|**adRsnDelete**|2|作業會刪除記錄。|  
|**adRsnFirstChange**|11|作業會對記錄中的第一項變更。|  
|**adRsnMove**|10|作業移動中的記錄指標**資料錄集**。|  
|**adRsnMoveFirst**|12|作業移至第一筆記錄的記錄指標**資料錄集**。|  
|**adRsnMoveLast**|15|作業移至最後一筆記錄的記錄指標**資料錄集**。|  
|**adRsnMoveNext**|13|作業移至下一筆記錄的記錄指標**資料錄集**。|  
|**adRsnMovePrevious**|14|作業移至前一個記錄中的記錄指標**資料錄集**。|  
|**adRsnRequery**|7|作業重新查詢[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)。|  
|**adRsnResynch**|8|重新同步處理作業**資料錄集**與資料庫。|  
|**adRsnUndoAddNew**|5|作業會反轉加入新的記錄。|  
|**adRsnUndoDelete**|6|作業會反轉刪除記錄。|  
|**adRsnUndoUpdate**|4|作業會反轉一筆記錄的更新。|  
|**adRsnUpdate**|3|作業會更新現有的記錄。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 Package: **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.EventReason.ADDNEW|  
|AdoEnums.EventReason.CLOSE|  
|AdoEnums.EventReason.DELETE|  
|AdoEnums.EventReason.FIRSTCHANGE|  
|AdoEnums.EventReason.MOVE|  
|AdoEnums.EventReason.MOVEFIRST|  
|AdoEnums.EventReason.MOVELAST|  
|AdoEnums.EventReason.MOVENEXT|  
|AdoEnums.EventReason.MOVEPREVIOUS|  
|AdoEnums.EventReason.REQUERY|  
|AdoEnums.EventReason.RESYNCH|  
|AdoEnums.EventReason.UNDOADDNEW|  
|AdoEnums.EventReason.UNDODELETE|  
|AdoEnums.EventReason.UNDOUPDATE|  
|AdoEnums.EventReason.UPDATE|  
  
## <a name="applies-to"></a>適用於  
  
|||  
|-|-|  
|[WillChangeRecord 和 RecordChangeComplete 事件 (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset 和 RecordsetChangeComplete 事件 (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillMove 和 MoveComplete 事件 (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)||
