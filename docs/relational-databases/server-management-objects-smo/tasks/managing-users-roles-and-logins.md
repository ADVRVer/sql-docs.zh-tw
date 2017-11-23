---
title: "管理使用者、 角色和登入 |Microsoft 文件"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
caps.latest.revision: "45"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eeda3dc5a30031545b7a6e500c378d6d4c190a6c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="managing-users-roles-and-logins"></a>管理使用者、角色和登入
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]在 SMO 中，登入都由<xref:Microsoft.SqlServer.Management.Smo.Login>物件。 當登入存在於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時，可以加入至伺服器角色。 伺服器角色由<xref:Microsoft.SqlServer.Management.Smo.ServerRole>物件。 資料庫角色是由 <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> 物件表示，應用程式角色則是由 <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> 物件表示。  
  
 伺服器層級相關聯的權限會列為屬性<xref:Microsoft.SqlServer.Management.Smo.ServerPermission>物件。 伺服器層級權限可授與個別的登入帳戶，也可從這些帳戶拒絕或撤銷。  
  
 每個<xref:Microsoft.SqlServer.Management.Smo.Database>物件具有<xref:Microsoft.SqlServer.Management.Smo.UserCollection>指定所有使用者資料庫中的物件。 每個使用者都與一個登入相關聯。 單一的登入可以與一個以上資料庫中的使用者產生關聯。 <xref:Microsoft.SqlServer.Management.Smo.Login>物件的<xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A>方法可以用來列出與登入相關聯的每個資料庫中所有使用者。 或者，<xref:Microsoft.SqlServer.Management.Smo.User> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Login> 屬性也可指定與該使用者相關的登入。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料庫也具有指定一組可讓使用者執行特定工作的資料庫層級權限的角色。 與伺服器角色不同的是，資料庫角色不是固定的。 這些角色可以建立、修改和移除。 若要進行大量管理，可以為資料庫角色指派權限和使用者。  
  
## <a name="example"></a>範例  
 在下列的程式碼範例中，您必須選取用於建立應用程式的程式設計環境、程式設計範本和程式設計語言。 如需詳細資訊，請參閱[建立 Visual C# 35。在 Visual Studio.NET 中的 SMO 專案](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a>在 Visual C# 中列舉登入和關聯的使用者  
 資料庫中的每個使用者都與一個登入相關聯。 此登入可以與一個以上資料庫中的使用者產生關聯。 此程式碼範例示範如何呼叫 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Login> 方法來列出與登入相關聯的所有資料庫使用者。 此範例會建立登入和使用者[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]以確保有可以列舉的對應資訊的資料庫。  
  
```csharp  
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a>在 PowerShell 中列舉登入和相關聯的使用者  
 資料庫中的每個使用者都與一個登入相關聯。 此登入可以與一個以上資料庫中的使用者產生關聯。 此程式碼範例示範如何呼叫 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Login> 方法來列出與登入相關聯的所有資料庫使用者。 此範例會建立登入和使用者[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]以確保有可以列舉的對應資訊的資料庫。  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database oject  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }  
  
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a>管理角色和使用者  
 此範例示範如何管理角色和使用者。 若要執行此範例，您必須參考下列組件：  
  
-   Microsoft.SqlServer.Smo.dll  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
-   Microsoft.SqlServer.ConnectionInfo.dll  
  
-   Microsoft.SqlServer.SqlEnum.dll  
  
```csharp  
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```
  
  
