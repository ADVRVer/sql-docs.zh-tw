---
title: "以程式設計方式處理事件 |Microsoft 文件"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: building-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Integration Services packages, events
- SQL Server Integration Services packages, events
- SSIS events, programmatically handling
- packages [Integration Services], events
- DtsEventHandler object
- SSIS packages, events
- SSIS events
- events [Integration Services], programmatically
- tasks [Integration Services], events
- IDTSEvents interface
ms.assetid: 0f00bd66-efd5-4f12-9e1c-36195f739332
caps.latest.revision: 47
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 7235703f494bd1fb50e696aef537391ba23d1749
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---
# <a name="handling-events-programmatically"></a>以程式設計方式處理事件
  [!INCLUDE[ssIS](../../includes/ssis-md.md)] 執行階段會提供在驗證和執行封裝之前、期間和之後所發生的事件集合。 這些事件可使用兩種方式來擷取。 第一個方法是藉由實作<xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents>介面類別中，並為參數，以提供類別**Execute**和**驗證**封裝的方法。 第二個方法是建立 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件，其中可包含當 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 內發生事件時所執行的其他 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 物件 (如工作和迴圈)。 本章節描述這兩個方法，並提供示範其使用方式的程式碼範例。  
  
## <a name="receiving-idtsevents-callbacks"></a>接收 IDTSEvents 回撥  
 以程式設計方式建立及執行封裝的開發人員，可以在驗證和執行程序期間使用 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 介面來接收事件通知。 這是藉由建立一個類別，實作<xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents>介面並提供此類別當做參數**驗證**和**Execute**封裝的方法。 然後當事件發生時，執行階段引擎會呼叫此類別的方法。  
  
 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 類別是一個已經實作 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 介面的類別；因此，直接實作 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 的另一個方法是衍生自 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents>，並覆寫您想要回應的特定事件。 然後提供您的類別當做參數**驗證**和**Execute**方法<xref:Microsoft.SqlServer.Dts.Runtime.Package>接收事件回撥。  
  
 下列程式碼範例會示範衍生自 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 的類別，並覆寫 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnPreExecute%2A> 方法。 類別然後依現狀來 aparameter**驗證**和**Execute**封裝的方法。  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      MyEventsClass eventsClass = new MyEventsClass();  
  
      p.Validate(null, null, eventsClass, null);  
      p.Execute(null, null, eventsClass, null, null);  
  
      Console.Read();  
    }  
  }  
  class MyEventsClass : DefaultEvents  
  {  
    public override void OnPreExecute(Executable exec, ref bool fireAgain)  
    {  
      // TODO: Add custom code to handle the event.  
      Console.WriteLine("The PreExecute event of the " +  
        exec.ToString() + " has been raised.");  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim eventsClass As MyEventsClass = New MyEventsClass()  
  
    p.Validate(Nothing, Nothing, eventsClass, Nothing)  
    p.Execute(Nothing, Nothing, eventsClass, Nothing, Nothing)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
Class MyEventsClass  
  Inherits DefaultEvents  
  
  Public Overrides Sub OnPreExecute(ByVal exec As Executable, ByRef fireAgain As Boolean)  
  
    ' TODO: Add custom code to handle the event.  
    Console.WriteLine("The PreExecute event of the " & _  
      exec.ToString() & " has been raised.")  
  
  End Sub  
  
End Class  
```  
  
## <a name="creating-dtseventhandler-objects"></a>建立 DtsEventHandler 物件  
 執行階段引擎會透過 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件提供功能強大且彈性高的事件處理和通知系統。 這些物件可讓您在事件處理常式內設計完整工作流程，只有當此事件處理常式所屬的事件發生時，才會執行這些工作流程。 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件是一個容器，當引發其父物件上的對應事件時會執行此物件。 此架構可讓您建立隔離的工作流程，執行這些工作流程是為了回應容器上所發生的事件。 因為 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件是同步的，所以要等到附加至此事件的事件處理常式傳回之後，才會繼續執行。  
  
 下列程式碼示範如何建立 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件。 此程式碼會將 <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> 加入至此封裝的 <xref:Microsoft.SqlServer.Dts.Runtime.Package.Executables%2A> 集合，然後為此工作的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 事件建立 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> 物件。 <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> 會加入至事件處理常式中，當第一個 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> 發生 <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> 事件時就會執行此事件處理常式。 這個範例假設您有一個名為 C:\Windows\Temp\DemoFile.txt 的檔案以供測試。 第一次執行此範例時，表示順利複製此檔案而且未呼叫此事件處理常式。 第二次執行此範例中，第一個<xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>將檔案複製失敗 (因為值<xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask.OverwriteDestinationFile%2A>是**false**)，呼叫事件處理常式時，第二個<xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>刪除原始程式檔和封裝報表失敗，因為發生錯誤。  
  
## <a name="example"></a>範例  
  
```csharp  
using System;  
using System.IO;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string f = "DemoFile.txt";  
      Executable e;  
      TaskHost th;  
      FileSystemTask fst;  
  
      Package p = new Package();  
  
      p.Variables.Add("sourceFile", true, String.Empty,  
        @"C:\Windows\Temp\" + f);  
      p.Variables.Add("destinationFile", true, String.Empty,  
        Path.Combine(Directory.GetCurrentDirectory(), f));  
  
      // Create a first File System task and add it to the package.  
      // This task tries to copy a file from one folder to another.  
      e = p.Executables.Add("STOCK:FileSystemTask");  
      th = e as TaskHost;  
      th.Name = "FileSystemTask1";  
      fst = th.InnerObject as FileSystemTask;  
  
      fst.Operation = DTSFileSystemOperation.CopyFile;  
      fst.OverwriteDestinationFile = false;  
      fst.Source = "sourceFile";  
      fst.IsSourcePathVariable = true;  
      fst.Destination = "destinationFile";  
      fst.IsDestinationPathVariable = true;  
  
      // Add an event handler for the FileSystemTask's OnError event.  
      DtsEventHandler ehOnError = (DtsEventHandler)th.EventHandlers.Add("OnError");  
  
      // Create a second File System task and add it to the event handler.  
      // This task deletes the source file if the event handler is called.  
      e = ehOnError.Executables.Add("STOCK:FileSystemTask");  
      th = e as TaskHost;  
      th.Name = "FileSystemTask2";  
      fst = th.InnerObject as FileSystemTask;  
  
      fst.Operation = DTSFileSystemOperation.DeleteFile;  
      fst.Source = "sourceFile";  
      fst.IsSourcePathVariable = true;  
  
      DTSExecResult vr = p.Validate(null, null, null, null);  
      Console.WriteLine("ValidationResult = " + vr.ToString());  
      if (vr == DTSExecResult.Success)  
      {  
        DTSExecResult er = p.Execute(null, null, null, null, null);  
        Console.WriteLine("ExecutionResult = " + er.ToString());  
        if (er == DTSExecResult.Failure)  
          if (!File.Exists(@"C:\Windows\Temp\" + f))  
            Console.WriteLine("Source file has been deleted by the event handler.");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim f As String = "DemoFile.txt"  
    Dim e As Executable  
    Dim th As TaskHost  
    Dim fst As FileSystemTask  
  
    Dim p As Package = New Package()  
  
    p.Variables.Add("sourceFile", True, String.Empty, _  
      "C:\Windows\Temp\" & f)  
    p.Variables.Add("destinationFile", True, String.Empty, _  
      Path.Combine(Directory.GetCurrentDirectory(), f))  
  
    ' Create a first File System task and add it to the package.  
    ' This task tries to copy a file from one folder to another.  
    e = p.Executables.Add("STOCK:FileSystemTask")  
    th = CType(e, TaskHost)  
    th.Name = "FileSystemTask1"  
    fst = CType(th.InnerObject, FileSystemTask)  
  
    fst.Operation = DTSFileSystemOperation.CopyFile  
    fst.OverwriteDestinationFile = False  
    fst.Source = "sourceFile"  
    fst.IsSourcePathVariable = True  
    fst.Destination = "destinationFile"  
    fst.IsDestinationPathVariable = True  
  
    ' Add an event handler for the FileSystemTask's OnError event.  
    Dim ehOnError As DtsEventHandler = CType(th.EventHandlers.Add("OnError"), DtsEventHandler)  
  
    ' Create a second File System task and add it to the event handler.  
    ' This task deletes the source file if the event handler is called.  
    e = ehOnError.Executables.Add("STOCK:FileSystemTask")  
    th = CType(e, TaskHost)  
    th.Name = "FileSystemTask1"  
    fst = CType(th.InnerObject, FileSystemTask)  
  
    fst.Operation = DTSFileSystemOperation.DeleteFile  
    fst.Source = "sourceFile"  
    fst.IsSourcePathVariable = True  
  
    Dim vr As DTSExecResult = p.Validate(Nothing, Nothing, Nothing, Nothing)  
    Console.WriteLine("ValidationResult = " + vr.ToString())  
    If vr = DTSExecResult.Success Then  
      Dim er As DTSExecResult = p.Execute(Nothing, Nothing, Nothing, Nothing, Nothing)  
      Console.WriteLine("ExecutionResult = " + er.ToString())  
      If er = DTSExecResult.Failure Then  
        If Not File.Exists("C:\Windows\Temp\" + f) Then  
          Console.WriteLine("Source file has been deleted by the event handler.")  
        End If  
      End If  
    End If  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services &#40;SSIS &#41;事件處理常式](../../integration-services/integration-services-ssis-event-handlers.md)   
 [將事件處理常式加入封裝](http://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  

