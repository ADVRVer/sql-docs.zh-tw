---
title: "Delete 方法 （ADO 欄位集合） |Microsoft 文件"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: de4e5f85bad4849f4ace2ee4e32fbe6606cb667d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-ado-fields-collection"></a>Delete 方法 （ADO 欄位集合）
刪除的物件從[欄位](../../../ado/reference/ado-api/fields-collection-ado.md)集合。  
  
## <a name="syntax"></a>語法  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>參數  
 *欄位*  
 A **Variant** ，其中指定[欄位](../../../ado/reference/ado-api/field-object.md)若要刪除的物件。 這個參數可以是名稱**欄位**物件或序數位置**欄位**物件本身。  
  
## <a name="remarks"></a>備註  
 呼叫**Fields.Delete**方法上開啟[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)會導致執行階段錯誤。  
  
## <a name="applies-to"></a>適用於  
 [欄位集合 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [Delete 方法 （ADO 參數集合）](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete 方法 （ADO 資料錄集）](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord 方法 (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)

