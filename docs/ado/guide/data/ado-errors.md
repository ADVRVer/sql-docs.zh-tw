---
title: ADO 錯誤 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO]
ms.assetid: 9bb84114-a1df-4122-a1b8-ad98dcd85cc3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2c357384a3de683c05b2922149e2b61630881922
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926206"
---
# <a name="ado-run-time-errors"></a>ADO 執行階段錯誤
ADO 錯誤會回報給您的程式，做為執行階段錯誤。 您可以使用程式設計語言的「錯誤捕捉」機制來加以攔截和處理。 例如，在 Visual Basic 中，使用**On Error**語句。 在 Visual C++ 中，這取決於您用來存取 ADO 程式庫的方法。 利用 #import，請使用**try-catch**區塊。 否則，c + + 程式設計人員必須藉由呼叫**GetErrorInfo**來明確取得錯誤物件。 下列 Visual Basic sub 程式示範如何捕捉 ADO 錯誤：

```
' BeginErrorHandlingVB01
Private Sub Form_Load()
' Turn on error handling
On Error GoTo FormLoadError

'Open the database and the recordset for processing.
'
Dim strCnn As String
strCnn = "Provider=sqloledb;" & _
    "Data Source=a-iresmi2000;" & _
    "Initial Catalog=Northwind;Integrated Security=SSPI"

' cnn is a Public Connection Object because
' it was defined WithEvents
Set cnn = New ADODB.Connection
cnn.Open strCnn

' The next line of code intentionally causes
' an error by trying to open a connection
' that has already been opened.
cnn.Open strCnn

' rst is a Public Recordset because it
' was defined WithEvents
Set rst = New ADODB.Recordset
rst.Open "Customers", cnn

Exit Sub

' Error handler
FormLoadError:
    Dim strErr As String
    Select Case Err
        Case adErrObjectOpen
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            strErr = strErr & "Error reported by: " & Err.Source & vbCrLf
            strErr = strErr & "Help File: " & Err.HelpFile & vbCrLf
            strErr = strErr & "Topic ID: " & Err.HelpContext
            MsgBox strErr
            Debug.Print strErr
            Err.Clear
            Resume Next
        ' If some other error occurs that
        ' has nothing to do with ADO, show
        ' the number and description and exit.
        Case Else
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            MsgBox strErr
            Debug.Print strErr
            Unload Me
    End Select
End Sub
' EndErrorHandlingVB01
```

 這個**Form_Load**事件程式會嘗試開啟相同的**連接**物件兩次，以刻意建立錯誤。 第二次呼叫**Open**方法時，會啟用錯誤處理常式。 在此情況下，錯誤的類型為**adErrObjectOpen**，因此錯誤處理常式會在繼續執行程式之前顯示下列訊息：

```
Error #3705: Operation is not allowed when the object is open.
Error reported by: ADODB.Connection
Help File: E:\WINNT\HELP\ADO260.CHM Topic ID: 1003705
```

 錯誤訊息包含 Visual Basic **Err**物件所提供的每一項資訊，但**LastDLLError**值除外，此處不適用。 錯誤號碼會告訴您發生了哪個錯誤。 當您不想要自行處理錯誤時，描述會很有用。 您可以直接將它傳遞給使用者。 雖然您通常會想要使用針對應用程式自訂的訊息，但您不能預期每個錯誤;描述會提供一些線索，說明發生錯誤的原因。 在範例程式碼中，**連接**物件報告了錯誤。 您會在這裡看到物件的類型或程式設計識別碼-不是變數名稱。

> [!NOTE]
>  Visual Basic **Err**物件只包含最新錯誤的相關資訊。 **連接**物件的 ADO **Errors**集合針對最近 ADO 作業引發的每個錯誤，各包含一個**錯誤**物件。 使用**Errors**集合，而不是**Err**物件來處理多個錯誤。 如需有關**錯誤**集合的詳細資訊，請參閱[提供者錯誤](../../../ado/guide/data/provider-errors.md)。 不過，如果沒有有效的**連接**物件，則**ERR**物件是 ADO 錯誤相關資訊的唯一來源。

 哪種作業可能會造成 ADO 錯誤？ 常見的 ADO 錯誤可能牽涉到開啟物件，例如**連接**或**記錄集**、嘗試更新資料，或呼叫提供者不支援的方法或屬性。

 OLE DB 錯誤也可以當做**錯誤**集合中的執行階段錯誤，傳遞至您的應用程式。

 下列主題提供 ADO 錯誤的詳細資訊。

-   [ADO 錯誤參考](../../../ado/guide/data/ado-error-reference.md)
