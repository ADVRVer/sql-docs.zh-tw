---
title: 批次方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- methods [Reporting Services], batches
- BatchHeader SOAP header
- Web service [Reporting Services], methods
- Report Server Web service, batching
- batches [Reporting Services]
- XML Web service [Reporting Services], methods
- locking [Reporting Services]
- multiple Web service methods
ms.assetid: 86435534-c9fe-4b49-b88c-7fb6d21976b0
caps.latest.revision: 35
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2c617c2a99399e71622962631d0f65ed70c9e9fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36136597"
---
# <a name="batching-methods"></a>批次方法
  在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中使用 SOAP 標頭可讓您在單一作業中包括多個 Web 服務方法。 方法會依呼叫它們的順序在單一資料庫交易的範圍中執行。  
  
 交易回復是使用多個方法批次作業的其中一個優點。 如果在呼叫任何方法時發生錯誤，報表伺服器會停止執行批次，並回復任何之前的作業。 當方法呼叫須視該批次中的其他方法呼叫是否成功完成時，這將會非常有用。  
  
 Web 服務並不會為多個方法批次作業提供鎖定語意。 在將訊息傳送到伺服器以及呼叫 Execute 命令之前，在報表伺服器資料庫中的資料列不會鎖定更新。  
  
 另外，也有並行控制項以保證資料庫自從上次讀取資料之後沒有任何變更。 如果有兩個用戶端修改相同的項目，當參數仍然有效 (例如，未重新命名項目) 時，則最後的更新會成功。  
  
 下列範例會呼叫 <xref:ReportService2005.ReportingService2005.CreateFolder%2A> 方法三次，並將以單一批次執行這些呼叫。 如果呼叫 <xref:ReportService2005.ReportingService2005.CreateFolder%2A> 失敗，則會取消整個批次。  
  
```vb  
Imports System  
Imports System.Web.Services.Protocols  
Imports myNamespace.MyReferenceName  
  
Class Sample  
    Sub Main(args() As String)  
        Dim rs As New ReportingService2005()  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      ' Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        Dim bh As New BatchHeader()  
  
        bh.BatchId = service.CreateBatch()  
        rs.BatchHeaderValue = bh  
        rs.CreateFolder("New Folder1", "/", Nothing)  
        rs.CreateFolder("New Folder2", "/", Nothing)  
        rs.CreateFolder("New Folder3", "/", Nothing)  
  
        Console.WriteLine("Creating folders...")  
        rs.BatchHeaderValue = bh  
        rs.ExecuteBatch()  
        Console.WriteLine("Folders created successfully.")  
  
        rs.BatchHeaderValue = Nothing  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Web.Services.Protocols;   
using myNamespace.MyReferenceName;  
  
class Sample  
{  
    static void Main(string[] args)  
    {  
        ReportingService2005 rs = new ReportingService2005();  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      // Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        BatchHeader bh = new BatchHeader();  
  
        bh1.BatchID = service.CreateBatch();  
        rs.BatchHeaderValue = bh;  
        rs.CreateFolder("New Folder1", "/", null);  
        rs.CreateFolder("New Folder2", "/", null);  
        rs.CreateFolder("New Folder3", "/", null);  
  
        Console.WriteLine("Creating folders...");  
        rs.BatchHeaderValue = bh1;  
        rs.ExecuteBatch();  
        Console.WriteLine("Folders created successfully.");  
  
        rs.BatchHeaderValue = null;  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:ReportService2005.ReportingService2005.CancelBatch%2A>   
 <xref:ReportService2005.ReportingService2005.CreateBatch%2A>   
 [技術參考 &#40;SSRS&#41;](../technical-reference-ssrs.md)   
 [使用 Reporting Services SOAP 標頭](using-reporting-services-soap-headers.md)  
  
  