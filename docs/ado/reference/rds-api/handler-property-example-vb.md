---
title: Handler 屬性範例 (VB) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Handler property [ADO], Visual Basic example
ms.assetid: 9664f9a6-65fc-4e7f-be3d-3e4b501b558a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1a72e393716d3d24fdb9f0f95be9faae85651696
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67964109"
---
# <a name="handler-property-example-vb"></a>Handler 屬性範例 (VB)
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件不會再包含在 Windows 作業系統中 (請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416)如需詳細資訊)。 RDS 用戶端元件將會在 Windows 的未來版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉至[WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
 此範例示範[RDS DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)物件[處理常式](../../../ado/reference/rds-api/handler-property-rds.md)屬性。 (請參閱[DataFactory 自訂](../../../ado/guide/remote-data-service/datafactory-customization.md)如需詳細資訊。)  
  
 假設下列各節中的參數檔案，Msdfmap.ini，位於伺服器上：  
  
```  
[connect AuthorDataBase]  
Access=ReadWrite  
Connect="DSN=Pubs"  
[sql AuthorById]  
SQL="SELECT * FROM Authors WHERE au_id = ?"  
```  
  
 您的程式碼看起來如下所示。 指派給命令[SQL](../../../ado/reference/rds-api/sql-property.md)屬性會比對***AuthorById***識別項，並將擷取的資料列，作者 Michael O'Leary。 **DataControl**物件**資料錄集**屬性會被指派至已中斷連線[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)純粹為程式碼撰寫的物件。  
  
```  
'BeginHandlerVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim dc As New DataControl  
    Dim rst As ADODB.Recordset  
  
    dc.Handler = "MSDFMAP.Handler"  
    dc.ExecuteOptions = 1  
    dc.FetchOptions = 1  
    dc.Server = "https://MyServer"  
    dc.Connect = "Data Source=AuthorDataBase"  
    dc.SQL = "AuthorById('267-41-2394')"  
    dc.Refresh                  'Retrieve the record  
    Set rst = dc.Recordset      'Use another Recordset as a convenience  
    Debug.Print "Author is '" & rst!au_fname & " " & rst!au_lname & "'"  
  
    ' clean up  
    If rst.State = adStateOpen Then rst.Close  
    Set rst = Nothing  
    Set dc = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rst Is Nothing Then  
        If rst.State = adStateOpen Then rst.Close  
    End If  
    Set rst = Nothing  
    Set dc = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndHandlerVB  
```  
  
## <a name="see-also"></a>另請參閱  
 [DataControl 物件 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Handler 屬性 (RDS)](../../../ado/reference/rds-api/handler-property-rds.md)


