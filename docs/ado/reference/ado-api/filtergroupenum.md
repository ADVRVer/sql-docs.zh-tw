---
title: FilterGroupEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
author: rothja
ms.author: jroth
ms.openlocfilehash: b7b6a8d449d27539100f467da1eea19ec42e0a72
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764509"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
指定要從[記錄集](../../../ado/reference/ado-api/recordset-object-ado.md)篩選的記錄群組。  
  
|持續性|值|描述|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|僅用於查看上次[刪除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)、重新[同步](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)或[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)呼叫所影響之記錄的篩選準則。|  
|**adFilterConflictingRecords**|5|用於查看上次批次更新失敗記錄的篩選準則。|  
|**adFilterFetchedRecords**|3|用來在目前的快取中查看記錄的篩選-也就是最後一次呼叫從資料庫取得記錄的結果。|  
|**adFilterNone**|0|移除目前的篩選準則，並還原所有記錄以進行查看。|  
|**adFilterPendingRecords**|1|僅用於查看已變更但尚未傳送到伺服器之記錄的篩選。 僅適用于批次更新模式。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等  
 Package： **.com. wfc. 資料**  
  
|持續性|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums. FilterGroup. NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>套用至  
 [Filter 屬性](../../../ado/reference/ado-api/filter-property.md)
