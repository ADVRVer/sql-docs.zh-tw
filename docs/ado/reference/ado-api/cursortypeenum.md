---
title: CursorTypeEnum | Microsoft Docs
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
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0e58e1d7660b4bcd014d5e4b80226fc9c3cfb293
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="cursortypeenum"></a>CursorTypeEnum
指定使用中的資料指標類型[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件。  
  
|常數|Value|Description|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|使用動態資料指標。 新增、 變更和其他使用者刪除是可見的以及透過移動的所有類型**資料錄集**允許，除了書籤，如果提供者不支援它們。|  
|**adOpenForwardOnly**|0|預設值。 使用順向資料指標。 與相同的靜態資料指標，不同之處在於您可以只捲動轉寄的記錄。 這可改善效能，當您需要只執行一次通過**資料錄集**。|  
|**adOpenKeyset**|1|使用索引鍵集資料指標。 要動態資料指標，不同之處在於您看不記錄，新增其他使用者，雖然其他使用者刪除的記錄都無法存取，從您**資料錄集**。 其他使用者的資料變更是仍然可見的。|  
|**adOpenStatic**|3|使用靜態資料指標，也就是靜態的一組可用來尋找資料，或產生報表記錄副本。 新增、 變更或刪除其他使用者不會顯示。|  
|**adOpenUnspecified**|-1|未指定資料指標的類型。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 Package: **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.CursorType.DYNAMIC|  
|AdoEnums.CursorType.FORWARDONLY|  
|AdoEnums.CursorType.KEYSET|  
|AdoEnums.CursorType.STATIC|  
|AdoEnums.CursorType.UNSPECIFIED|  
  
## <a name="applies-to"></a>適用於  
 [CursorType 屬性 (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
