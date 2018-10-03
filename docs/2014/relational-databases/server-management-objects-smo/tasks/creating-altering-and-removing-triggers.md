---
title: 建立、 改變和移除觸發程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2ae7ab9d88a407f298156ebeafdb6ec5d70198b1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220638"
---
# <a name="creating-altering-and-removing-triggers"></a>建立、改變和移除觸發程式
  在 SMO 中，觸發程序是利用 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 物件表示。 [!INCLUDE[tsql](../../../includes/tsql-md.md)]時，會引發觸發程序由設定執行程式碼<xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A>觸發程序物件的屬性。 觸發程序的類型是利用 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 物件的其他屬性所設定，例如 <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> 屬性。 這是布林值屬性，指定觸發程序是否由記錄的 `UPDATE` 在父資料表上引發。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 物件代表傳統的資料操作語言 (DML) 觸發程式。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和更新版本也支援資料定義語言 (DDL) 觸發程序。 DDL 觸發程序是由 <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> 物件和 <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> 物件表示。  
  
## <a name="example"></a>範例  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a>在 Visual Basic 中建立、改變和移除觸發程序  
 此程式碼範例示範如何在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫中名為 `Sales` 的現有資料表上，建立及插入更新觸發程序。 此觸發程序會在資料表更新或新記錄插入時傳送提醒訊息。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTriggers1](SMO How to#SMO_VBTriggers1)]  -->  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a>在 Visual C# 中建立、改變和移除觸發程序  
 此程式碼範例示範如何在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫中名為 `Sales` 的現有資料表上，建立及插入更新觸發程序。 此觸發程序會在資料表更新或新記錄插入時傳送提醒訊息。  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a>在 PowerShell 中建立、改變和移除觸發程序  
 此程式碼範例示範如何在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫中名為 `Sales` 的現有資料表上，建立及插入更新觸發程序。 此觸發程序會在資料表更新或新記錄插入時傳送提醒訊息。  
  
```  
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = get-item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger `  
-argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.   
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.   
$tr.Create()  
  
#Remove the trigger.   
$tr.Drop()  
```  
  
  
