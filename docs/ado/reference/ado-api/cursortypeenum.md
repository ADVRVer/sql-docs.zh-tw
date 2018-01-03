---
title: "CursorTypeEnum |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: CursorTypeEnum
helpviewer_keywords: CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: a84a48381c8c08f8b49e2ec9390366135f53b46f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cursortypeenum"></a>CursorTypeEnum
指定使用中的資料指標類型[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件。  
  
|常數|ReplTest1|描述|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|使用動態資料指標。 新增、 變更和其他使用者刪除是可見的以及透過移動的所有類型**資料錄集**允許，除了書籤，如果提供者不支援它們。|  
|**adOpenForwardOnly**|0|預設值。 使用順向資料指標。 與相同的靜態資料指標，不同之處在於您可以只捲動轉寄的記錄。 這可改善效能，當您需要只執行一次通過**資料錄集**。|  
|**adOpenKeyset**|@shouldalert|使用索引鍵集資料指標。 要動態資料指標，不同之處在於您看不記錄，新增其他使用者，雖然其他使用者刪除的記錄都無法存取，從您**資料錄集**。 其他使用者的資料變更是仍然可見的。|  
|**adOpenStatic**|3|使用靜態資料指標，也就是靜態的一組可用來尋找資料，或產生報表記錄副本。 新增、 變更或刪除其他使用者不會顯示。|  
|**adOpenUnspecified**|-1|未指定資料指標的類型。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.CursorType.DYNAMIC|  
|AdoEnums.CursorType.FORWARDONLY|  
|AdoEnums.CursorType.KEYSET|  
|AdoEnums.CursorType.STATIC|  
|AdoEnums.CursorType.UNSPECIFIED|  
  
## <a name="applies-to"></a>適用於  
 [CursorType 屬性 (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
