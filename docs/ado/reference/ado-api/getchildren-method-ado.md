---
title: GetChildren 方法 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 910977912a23ee48f740afccdb58c6f82801f2a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028106"
---
# <a name="getchildren-method-ado"></a>GetChildren 方法 (ADO)
傳回[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)其資料列代表集合的子系[記錄](../../../ado/reference/ado-api/record-object-ado.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>傳回值  
 A **Recordset**物件的每個資料列都代表目前的子系**記錄**物件。 例如的子系**記錄**代表目錄是檔案，以及包含在父目錄的子目錄。  
  
## <a name="remarks"></a>備註  
 提供者會決定哪些資料行存在於所傳回**資料錄集**。 例如，文件的來源提供者一律會傳回資源**資料錄集**。  
  
## <a name="applies-to"></a>適用於  
  
|||  
|-|-|  
|[Record 物件 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
