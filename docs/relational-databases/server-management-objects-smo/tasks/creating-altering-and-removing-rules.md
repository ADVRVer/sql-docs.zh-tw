---
title: 建立、 改變和移除規則 |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rules [SMO]
ms.assetid: 16981459-524e-4b39-a899-4370eaf763cc
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ee31d91f1881b0ed7c8159c22cffa89af4c20bc7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43075631"
---
# <a name="creating-altering-and-removing-rules"></a>建立、改變和移除規則
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  在 SMO 中，規則會以 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件表示， 並由 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 屬性定義，該屬性是文字字串，包含使用運算子或述詞 (例如 IN、LIKE 或 BETWEEN) 的條件運算式。 規則不能參考資料行或其他資料庫物件。 未參考資料庫物件的內建函數可以包括在內。  
  
 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 屬性中的定義必須包含參考所輸入之資料值的變數。 任何名稱或符號可用來代表值，當建立規則，但第一個字元必須是\@符號。  
  
## <a name="example"></a>範例  
 如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。 如需詳細資訊，請參閱 <<c0> [ 建立 Visual C&#35; Visual Studio.NET 中的 SMO 專案](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</c0>  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-basic"></a>在 Visual Basic 中建立、改變和移除規則  
 此程式碼範例示範如何建立規則、將規則附加至資料行、修改 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件的屬性、將規則從資料行卸離，然後再加以卸除。  
  
 **Dim**陳述式<xref:Microsoft.SqlServer.Management.Smo.Rule>使用完整組件路徑，以避免模稜兩可，與指定物件<xref:Microsoft.SqlServer.Management.Smo.Rule>System.Data 組件中的物件。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Declare a Table object variable and reference the Product table.
Dim tb As Table
tb = db.Tables("Product", "Production")
'Define a Rule object variable by supplying the parent database, name and schema in the constructor. 
'Note that the full namespace must be given for the Rule type to differentiate it from other Rule types.
Dim ru As Microsoft.SqlServer.Management.Smo.Rule
ru = New Rule(db, "TestRule", "Production")
'Set the TextHeader and TextBody properties to define the rule.
ru.TextHeader = "CREATE RULE [Production].[TestRule] AS"
ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())"
'Create the rule on the instance of SQL Server.
ru.Create()
'Bind the rule to a column in the Product table by supplying the table, schema, and 
'column as arguments in the BindToColumn method.
ru.BindToColumn("Product", "SellEndDate", "Production")
'Unbind from the column before removing the rule from the database.
ru.UnbindFromColumn("Product", "SellEndDate", "Production")
ru.Drop()
```
  
## <a name="creating-altering-and-removing-a-rule-in-visual-c"></a>在 Visual C# 中建立、改變和移除規則  
 此程式碼範例示範如何建立規則、將規則附加至資料行、修改 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件的屬性、將規則從資料行卸離，然後再加以卸除。  
  
 **Dim**陳述式<xref:Microsoft.SqlServer.Management.Smo.Rule>使用完整組件路徑，以避免模稜兩可，與指定物件<xref:Microsoft.SqlServer.Management.Smo.Rule>System.Data 組件中的物件。  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
            //Note that the full namespace must be given for the Rule type to differentiate it from other Rule types.   
            Microsoft.SqlServer.Management.Smo.Rule ru;  
            ru = new Rule(db, "TestRule", "Production");  
            //Set the TextHeader and TextBody properties to define the rule.   
            ru.TextHeader = "CREATE RULE [Production].[TestRule] AS";  
            ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())";  
            //Create the rule on the instance of SQL Server.   
            ru.Create();  
            //Bind the rule to a column in the Product table by supplying the table, schema, and   
            //column as arguments in the BindToColumn method.   
            ru.BindToColumn("Product", "SellEndDate", "Production");  
            //Unbind from the column before removing the rule from the database.   
            ru.UnbindFromColumn("Product", "SellEndDate", "Production");  
            ru.Drop();  
  
        }  
```  
  
## <a name="creating-altering-and-removing-a-rule-in-powershell"></a>在 PowerShell 中建立、改變和移除規則  
 此程式碼範例示範如何建立規則、將規則附加至資料行、修改 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件的屬性、將規則從資料行卸離，然後再加以卸除。  
  
 **Dim**陳述式<xref:Microsoft.SqlServer.Management.Smo.Rule>使用完整組件路徑，以避免模稜兩可，與指定物件<xref:Microsoft.SqlServer.Management.Smo.Rule>System.Data 組件中的物件。  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
$ru = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Rule `  
-argumentlist $db, "TestRule", "Production"  
  
#Set the TextHeader and TextBody properties to define the rule.   
$ru.TextHeader = "CREATE RULE [Production].[TestRule] AS"  
$ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())"  
  
#Create the rule on the instance of SQL Server.   
$ru.Create()  
  
# Bind the rule to a column in the Product table by supplying the table, schema, and   
# column as arguments in the BindToColumn method.   
$ru.BindToColumn("Product", "SellEndDate", "Production")  
  
#Unbind from the column before removing the rule from the database.   
$ru.UnbindFromColumn("Product", "SellEndDate", "Production")  
$ru.Drop()  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.SqlServer.Management.Smo.Rule>  
  
  
