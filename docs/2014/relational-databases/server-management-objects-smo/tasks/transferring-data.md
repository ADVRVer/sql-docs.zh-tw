---
title: 將資料傳輸 |Microsoft 文件
ms.custom: ''
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- data transfers [SMO]
- transferring data
ms.assetid: eea255c3-8251-40f0-973b-fe4ef6cb5261
caps.latest.revision: 49
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dc0b4f2e79564bbdc6ceaabb088cdb070636a3d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36036329"
---
# <a name="transferring-data"></a>傳送資料
  <xref:Microsoft.SqlServer.Management.Smo.Transfer> 類別是一種公用程式類別，可提供工具來傳送物件和資料。  
  
 資料庫結構描述中物件的傳送方式是藉由執行目標伺服器上產生的指令碼。 <xref:Microsoft.SqlServer.Management.Smo.Table> 資料會隨著動態建立的 DTS 封裝一起傳送。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件包含了 DMO 中 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件的所有功能和其他 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。 不過，在 SMO 中[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]、<xref:Microsoft.SqlServer.Management.Smo.Transfer>物件會使用[SQLBulkCopy](http://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy\(v=VS.90\).aspx) API 來傳送資料。 此外，用來執行資料傳送的方法和屬性是位於 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件上，而不是 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件上。 將功能從執行個體類別移到公用程式類別與較輕的物件模型一致，因為只有在需要時才會載入特定工作的程式碼。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件不支援將資料傳送到 <xref:Microsoft.SqlServer.Management.Smo.Database.CompatibilityLevel%2A> 小於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體版本的目標資料庫。  
  
## <a name="example"></a>範例  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-basic"></a>在 Visual Basic 中將結構描述和資料從某個資料庫傳送到另一個資料庫  
 此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件，將結構描述和資料從某個資料庫傳送到另一個資料庫。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Create a new database that is to be destination database.
Dim dbCopy As Database
dbCopy = New Database(srv, "AdventureWorks2012Copy")
dbCopy.Create()
'Define a Transfer object and set the required options and properties.
Dim xfr As Transfer
xfr = New Transfer(db)
xfr.CopyAllTables = True
xfr.Options.WithDependencies = True
xfr.Options.ContinueScriptingOnError = True
xfr.DestinationDatabase = "AdventureWorks2012Copy"
xfr.DestinationServer = srv.Name
xfr.DestinationLoginSecure = True
xfr.CopySchema = True
'Script the transfer. Alternatively perform immediate data transfer with TransferData method.
xfr.ScriptTransfer()
```
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-c"></a>在 Visual C# 中將結構描述和資料從某個資料庫傳送到另一個資料庫  
 此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件，將結構描述和資料從某個資料庫傳送到另一個資料庫。  
  
```  
{  
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Create a new database that is to be destination database.   
            Database dbCopy;  
            dbCopy = new Database(srv, "AdventureWorks2012Copy");  
            dbCopy.Create();  
            //Define a Transfer object and set the required options and properties.   
            Transfer xfr;  
            xfr = new Transfer(db);  
            xfr.CopyAllTables = true;  
            xfr.Options.WithDependencies = true;  
            xfr.Options.ContinueScriptingOnError = true;  
            xfr.DestinationDatabase = "AdventureWorks2012Copy";  
            xfr.DestinationServer = srv.Name;  
            xfr.DestinationLoginSecure = true;  
            xfr.CopySchema = true;  
            //Script the transfer. Alternatively perform immediate data transfer   
            // with TransferData method.   
            xfr.ScriptTransfer();  
        }   
```  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-powershell"></a>在 PowerShell 中將結構描述和資料從某個資料庫傳送到另一個資料庫  
 此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件，將結構描述和資料從某個資料庫傳送到另一個資料庫。  
  
```  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Reference the AdventureWorks2012 database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a database to hold the copy of AdventureWorks  
$dbCopy = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Database -argumentlist $srv, "AdventureWorksCopy"  
$dbCopy.Create()  
  
#Define a Transfer object and set the required options and properties.  
$xfr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Transfer -argumentlist $db  
  
#Set this objects properties  
$xfr.CopyAllTables = $true  
$xfr.Options.WithDependencies = $true  
$xfr.Options.ContinueScriptingOnError = $true  
$xfr.DestinationDatabase = "AdventureWorksCopy"  
$xfr.DestinationServer = $srv.Name  
$xfr.DestinationLoginSecure = $true  
$xfr.CopySchema = $true  
"Scripting Data Transfer"  
#Script the transfer. Alternatively perform immediate data transfer with TransferData method.  
$xfr.ScriptTransfer()  
```  
  
  