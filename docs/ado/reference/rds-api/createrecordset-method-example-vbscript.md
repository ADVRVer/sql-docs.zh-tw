---
title: CreateRecordset 方法範例 (VBScript) |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- CreateRecordset method [RDS], VBScript example
ms.assetid: cce0d8b5-e87b-4f7b-a8a0-37d5025a1f5d
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 752651b81e00e2d4f03e2e8b5a72acefc4fc1b30
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35287598"
---
# <a name="createrecordset-method-example-vbscript"></a>CreateRecordset 方法範例 (VBScript)
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件已不再包含在 Windows 作業系統中 (請參閱 < Windows 8 和[Windows Server 2012 相容性手冊](https://www.microsoft.com/en-us/download/details.aspx?id=27416)如需詳細資訊)。 Windows 的未來版本將移除 RDS 用戶端元件。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉到[WCF 資料服務](http://go.microsoft.com/fwlink/?LinkId=199565)。  
  
 這個程式碼範例會建立[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)伺服器端上。 它有兩個資料行的四個資料列。 剪下和貼上下列程式碼，[記事本] 或其他文字編輯器，並將它儲存成**CreateRecordsetVBS.asp**。  
  
```  
<!-- BeginCreateRecordsetVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>CreateRecordset Method Example (VBScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body>  
  
<OBJECT classid=clsid:BD96C556-65A3-11D0-983A-00C04FC29E33 height=1 id=DC1 width=1>  
</OBJECT>  
<h1>CreateRecordset Method Example (VBScript)</h1>  
<script language = "vbscript">  
    ' use the RDS.DataControl to create an empty recordset;   
    ' takes an array of variants where every element is itself another  
    ' array of variants, one for every column required in the recordset  
  
    ' the elements of the inner array are the column's  
    ' name, type, size, and nullability  
Sub GetRS()  
   Dim Record(2)  
   Dim Field1(3)  
   Dim Field2(3)  
   Dim Field3(3)  
  
    ' for each field, specify the name type, size, and nullability  
  
   Field1(0) = "Name"   ' Column name.  
   Field1(1) = CInt(129)   ' Column type.  
   Field1(2) = CInt(40)   ' Column size.  
   Field1(3) = False      ' Nullable?  
  
   Field2(0) = "Age"  
   Field2 (1) = CInt(3)  
   Field2 (2) = CInt(-1)  
   Field2 (3) = True  
  
   Field3 (0) = "DateOfBirth"  
   Field3 (1) = CInt(7)  
   Field3 (2) = CInt(-1)  
   Field3 (3) = True  
  
    ' put all fields into an array of arrays  
   Record(0) = Field1  
   Record(1) = Field2  
   Record(2) = Field3  
  
   Dim NewRs   
   Set NewRS = DC1.CreateRecordset(Record)  
  
   Dim fields(2)  
   fields(0) = Field1(0)  
   fields(1) = Field2(0)  
   fields(2) = Field3(0)  
  
    ' Populate the new recordset with data values.  
   Dim fieldVals(2)  
  
    ' Use AddNew to add the records.  
   fieldVals(0) = "Joe"  
   fieldVals(1) = 5  
   fieldVals(2) = CDate(#1/5/96#)  
   NewRS.AddNew fields, fieldVals  
  
   fieldVals(0) = "Mary"  
   fieldVals(1) = 6  
   fieldVals(2) = CDate(#6/5/94#)  
   NewRS.AddNew fields, fieldVals  
  
   fieldVals(0) = "Alex"  
   fieldVals(1) = 13  
   fieldVals(2) = CDate(#1/6/88#)  
   NewRS.AddNew fields, fieldVals  
  
   fieldVals(0) = "Susan"  
   fieldVals(1) = 13  
   fieldVals(2) = CDate(#8/6/87#)  
   NewRS.AddNew fields, fieldVals  
  
   NewRS.MoveFirst  
  
    ' Set the newly created and populated Recordset to  
    ' the SourceRecordset property of the  
    ' RDS.DataControl to bind to visual controls  
  
   Set DC1.SourceRecordset = NewRS  
End Sub  
</script>  
<table datasrc="#DC1" align="center">  
<thead>  
<tr id="ColHeaders" class="thead2">  
   <th>Name</th>  
   <th>Age</th>  
    <th>D.O.B.</th>  
</tr>  
</thead>  
<tbody class="tbody">  
<tr>  
   <td><input datafld="Name" size=15 id=text1 name=text1> </td>  
   <td><input datafld="Age" size=25 id=text2 name=text2> </td>  
   <td><input datafld="DateOfBirth" size=25 id=text3 name=text3> </td>  
</tr>  
</tbody>  
</table>  
<input type = "button" onclick = "GetRS()" value="Go!">  
</body>  
</html>  
<!-- EndCreateRecordsetVBS -->  
```  
  
## <a name="see-also"></a>另請參閱  
 [CreateRecordset 方法 (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)   
 [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)


