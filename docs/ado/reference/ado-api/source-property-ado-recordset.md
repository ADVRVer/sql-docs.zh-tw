---
title: "來源屬性 （ADO 資料錄集） |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- Recordset15::putref_Source
- Recordset15::Source
- Recordset15::PutSource
- Recordset15::get_Source
- Recordset15::GetSource
- Recordset15::PutRefSource
- Recordset15::put_Source
helpviewer_keywords:
- Source property [ADO Recordset]
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ea45eae107fa55355adeb195e7e4fc5cf0a3c762
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="source-property-ado-recordset"></a>來源屬性 （ADO 資料錄集）
指出資料來源[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定**字串**值或[命令](../../../ado/reference/ado-api/command-object-ado.md)物件參考; 只會傳回**字串**值，指出來源**資料錄集**。  
  
## <a name="remarks"></a>備註  
 使用**來源**屬性，以指定的資料來源**資料錄集**物件使用下列其中之一：**命令**物件變數的 SQL 陳述式、 預存程序，或資料表名稱。  
  
 如果您設定**來源**屬性**命令**物件[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)屬性**資料錄集**物件就會繼承值**ActiveConnection**屬性所指定**命令**物件。 不過，讀取**來源**屬性不會傳回**命令**物件; 相反地，它會傳回[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)屬性**命令**物件至用以設定**來源**屬性。  
  
 如果**來源**屬性為 SQL 陳述式、 預存程序或資料表名稱，您可以藉由傳遞適當的最佳化效能*選項*引數與[開啟](../../../ado/reference/ado-api/open-method-ado-recordset.md)方法呼叫。  
  
 **來源**屬性是讀/寫關閉**資料錄集**物件或唯讀狀態開啟**資料錄集**物件。  
  
## <a name="applies-to"></a>適用於  
 [資料錄集物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [來源屬性範例 (VB)](../../../ado/reference/ado-api/source-property-example-vb.md)   
 [來源屬性 （ADO 錯誤）](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [來源屬性 （ADO 資料錄）](../../../ado/reference/ado-api/source-property-ado-record.md)

