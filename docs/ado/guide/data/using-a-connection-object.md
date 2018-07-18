---
title: 使用連接物件 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 4b34f971-5699-43e7-9b15-137d334fa66e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e04067cda6fad31ebd07f5d887e387139c7739b1
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979770"
---
# <a name="using-a-connection-object"></a>使用連接物件
開始前**連線**物件時，您必須定義有關資料來源和連線類型的特定資訊。 大部分的這項資訊由持有*ConnectionString*的參數[Open 方法](../../../ado/reference/ado-api/open-method-ado-connection.md)上**連接**物件，或由[ConnectionString屬性](../../../ado/reference/ado-api/connectionstring-property-ado.md)上**連線**物件。 連接字串是由單引號括住的值以分號分隔，引數/值組的清單所組成。 例如：  
  
```  
Dim sConn As String  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
```  
  
> [!NOTE]
>  您也可以指定 ODBC 資料來源名稱 (DSN) 或資料連結 (UDL) 檔案中的連接字串。 如需有關名稱 （dsn） 的詳細資訊，請參閱[管理的資料來源](../../../odbc/admin/managing-data-sources.md)ODBC 程式設計人員參考中。 如需 Udl 的詳細資訊，請參閱[資料連結 API 概觀](http://msdn.microsoft.com/95c180ea-bd4f-4dca-b95a-576afd135bbc)OLE DB 程式設計人員參考中。  
  
 一般而言，您藉由呼叫，會在建立連線時**Connection.Open**方法，以適當*連接字串*做為其參數。 範例是以下列 Visual Basic 程式碼片段所示：  
  
```  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
' Open a connection.  
Set oConn = New ADODB.Connection  
.Open   
  
' Make a query over the connection.  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, , adOpenStatic, adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
' Close the connection.  
oConn.Close  
Set oConn = Nothing  
  
```  
  
 以下**oRs.Open**採用**連線**物件 (*oConn*) 變數的值設定為其*ActiveConnection*參數。 此外， **Connection.CursorLocation**屬性的預設值會假設**adUseServer**。 若要與此相反[HelloData](../../../ado/guide/data/hellodata-a-simple-ado-application.md)上一節的範例。 下列指示會導致執行階段錯誤。  
  
```  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
```
