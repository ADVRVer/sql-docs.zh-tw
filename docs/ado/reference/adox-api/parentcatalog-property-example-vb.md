---
description: ParentCatalog 屬性範例 (VB)
title: " (VB) 的 ParentCatalog 屬性範例 |Microsoft Docs"
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
- ParentCatalog property [ADOX], Visual Basic example
ms.assetid: 448bc850-7584-4c5f-89f3-5f4fee88b259
author: rothja
ms.author: jroth
ms.openlocfilehash: 6910ac229d309360676f83f855664ab368459ce0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983819"
---
# <a name="parentcatalog-property-example-vb"></a>ParentCatalog 屬性範例 (VB)
下列程式碼示範如何使用 [ParentCatalog](./parentcatalog-property-adox.md) 屬性來存取提供者特定的屬性，然後再將資料表附加至目錄。 屬性是 **自動遞增**的，會在 Microsoft Jet 資料庫中建立自動遞增欄位。  
  
```  
' BeginCreateAutoIncrColumnVB  
Sub Main()  
    On Error GoTo CreateAutoIncrColumnError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tbl As New ADOX.Table  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
  
    With tbl  
        .Name = "MyContacts"  
        Set .ParentCatalog = cat  
        ' Create fields and append them to the new Table object.  
        .Columns.Append "ContactId", adInteger  
        ' Make the ContactId column and auto incrementing column  
        .Columns("ContactId").Properties("AutoIncrement") = True  
        .Columns.Append "CustomerID", adVarWChar  
        .Columns.Append "FirstName", adVarWChar  
        .Columns.Append "LastName", adVarWChar  
        .Columns.Append "Phone", adVarWChar, 20  
        .Columns.Append "Notes", adLongVarWChar  
    End With  
  
    cat.Tables.Append tbl  
    Debug.Print "Table 'MyContacts' is added."  
  
    ' Delete the table as this is a demonstration.  
    cat.Tables.Delete tbl.Name  
    Debug.Print "Table 'MyContacts' is delete."  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set tbl = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CreateAutoIncrColumnError:  
  
    Set cat = Nothing  
    Set tbl = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
' EndCreateAutoIncrColumnVB  
```  
  
## <a name="see-also"></a>另請參閱  
 [將方法附加至 ADOX 資料行 () ](./append-method-adox-columns.md)   
 [附加方法 (ADOX 資料表) ](./append-method-adox-tables.md)   
 [ (ADOX) 的目錄物件 ](./catalog-object-adox.md)   
 [資料行物件 (ADOX) ](./column-object-adox.md)   
 [資料行集合 (ADOX) ](./columns-collection-adox.md)   
 [名稱屬性 (ADOX) ](./name-property-adox.md)   
 [ParentCatalog 屬性 (ADOX) ](./parentcatalog-property-adox.md)   
 [資料表物件 (ADOX) ](./table-object-adox.md)   
 [Type 屬性 (Column) (ADOX)](./type-property-column-adox.md)