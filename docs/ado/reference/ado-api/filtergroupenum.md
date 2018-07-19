---
title: FilterGroupEnum |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd0af463cf9ebc5bad28665cad32fc49fce5fb5b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278647"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
指定要從篩選的記錄群組[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)。  
  
|常數|ReplTest1|描述|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|篩選器來檢視記錄，最後會受到[刪除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)，[重新同步處理](../../../ado/reference/ado-api/resync-method.md)， [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)，或[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)呼叫。|  
|**adFilterConflictingRecords**|5|檢視失敗，最後一個批次更新記錄的篩選條件。|  
|**adFilterFetchedRecords**|3|在目前的快取中檢視記錄的篩選器 — 也就是從資料庫擷取記錄的最後一個呼叫的結果。|  
|**adFilterNone**|0|移除目前的篩選條件，並還原所有記錄的檢視。|  
|**adFilterPendingRecords**|@shouldalert|篩選器來檢視只記錄已變更但尚未傳送到伺服器。 僅適用於批次更新模式。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>適用於  
 [Filter 屬性](../../../ado/reference/ado-api/filter-property.md)
