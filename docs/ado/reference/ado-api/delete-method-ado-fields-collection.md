---
title: Delete 方法 (ADO Fields 集合) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 097286f14de4dead4490c322615a6405c157f118
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47768386"
---
# <a name="delete-method-ado-fields-collection"></a>Delete 方法 (ADO Fields 集合)
刪除的物件[欄位](../../../ado/reference/ado-api/fields-collection-ado.md)集合。  
  
## <a name="syntax"></a>語法  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>參數  
 *欄位*  
 A **Variant** ，其中指定[欄位](../../../ado/reference/ado-api/field-object.md)若要刪除的物件。 這個參數可以是名稱**欄位**物件或的序數位置**欄位**物件本身。  
  
## <a name="remarks"></a>備註  
 呼叫**Fields.Delete**方法，在開啟[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)會造成執行階段錯誤。  
  
## <a name="applies-to"></a>適用於  
 [Fields 集合 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [Delete 方法 （ADO Parameters 集合）](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete 方法 (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord 方法 (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
