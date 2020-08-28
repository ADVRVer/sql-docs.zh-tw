---
description: Status 屬性範例 (Field) (VB)
title: Status 屬性範例 (欄位)  (VB) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
author: rothja
ms.author: jroth
ms.openlocfilehash: 23a6ebaa724e06ce4a8283b95e3d7a982c8deef1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988690"
---
# <a name="status-property-example-field-vb"></a>Status 屬性範例 (Field) (VB)
下列範例會使用 [網際網路發佈提供者](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)，從讀取/寫入資料夾開啟檔。 [記錄](./record-object-ado.md)[欄位](./field-object.md)物件的[Status](./status-property-ado-field.md)屬性會先設定為**adFieldPendingInsert**，然後再更新為**adFieldOk**。  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=https://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 下列範例會從檔中開啟的**記錄**中，刪除已知的**欄位**。 **Status**屬性會先設定為**AdFieldOK**，然後**adFieldPendingUnknown**。  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 下列程式碼會從唯讀檔案上開啟的**記錄**中刪除**欄位**。 **狀態** 會設為 **adFieldPendingDelete**。 在 [更新](./update-method.md)時，刪除將會失敗，且 **狀態** 將會是 **adFieldPendingDelete** 加上 **adFieldPermissionDenied**。 [CancelUpdate](./cancelupdate-method-ado.md) 會清除擱置 **狀態** 設定。  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>另請參閱  
 [Field 物件](./field-object.md)   
 [ (ADO) 的記錄物件 ](./record-object-ado.md)   
 [Status 屬性 (ADO Field)](./status-property-ado-field.md)