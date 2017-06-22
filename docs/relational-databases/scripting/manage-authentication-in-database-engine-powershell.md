---
title: "管理資料庫引擎 PowerShell 中的驗證 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 135580dd67315ad9eb07361dcff7b1334398a0aa
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="manage-authentication-in-database-engine-powershell"></a>管理 Database Engine PowerShell 中的驗證
  依預設，連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時， [!INCLUDE[ssDE](../../includes/ssde-md.md)]PowerShell 元件會使用 Windows 驗證。 藉由定義 PowerShell 虛擬磁碟機，或指定 **Invoke-Sqlcmd** 的 **–Username** 和 **–Password**參數，即可使用 SQL Server 驗證。  
  
1.  **開始之前：**  [Permissions](#Permissions)  
  
2.  **使用下列項目，設定驗證：**[虛擬磁碟機](#SQLAuthVirtDrv)、[Invoke-Sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="Permissions"></a> Permissions  
 您在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體中可執行的所有動作，都是透過授與用來連接至執行個體之驗證認證的權限所控制。 依預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供者和 Cmdlet 會使用用來建立 [!INCLUDE[ssDE](../../includes/ssde-md.md)]之 Windows 驗證連接的 Windows 帳戶。  
  
 若要進行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接，您必須提供 SQL Server 驗證登入識別碼和密碼。 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供者時，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入認證與虛擬磁碟機產生關聯，然後使用變更目錄命令 (**cd**) 連接到該磁碟機。 在 Windows PowerShell 中，安全性認證只能與虛擬磁碟機產生關聯。  
  
##  <a name="SQLAuthVirtDrv"></a> 使用虛擬磁碟機的 SQL Server 驗證  
 **建立與 SQL Server 驗證登入相關聯的虛擬磁碟機**  
  
1.  建立的函數：  
  
    1.  具有參數可表示提供給虛擬磁碟機的名稱、登入識別碼，以及與虛擬磁碟機相關聯的提供者路徑。  
  
    2.  使用 **read-host** 提示使用者輸入密碼。  
  
    3.  使用 **new-object** 建立認證物件。  
  
    4.  使用 **new-psdrive** 建立具有已提供認證的虛擬磁碟機。  
  
2.  呼叫此函數，以建立具有已提供認證的虛擬磁碟機。  
  
### <a name="example-virtual-drive"></a>範例 (虛擬磁碟機)  
 此範例會建立名為 **sqldrive** 的函數，可讓您用來建立與指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入和執行個體相關聯的虛擬磁碟機。  
  
 **sqldrive** 函數會提示您輸入登入的密碼，並且在您輸入時遮罩密碼。 然後，每當您使用變更目錄命令 (**cd**) 連接到使用虛擬磁碟機名稱的路徑時，系統就會使用您在建立磁碟機時所提供的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入認證來執行所有作業。  
  
```  
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = read-host -AsSecureString -Prompt "Password"  
    $cred = new-object System.Management.Automation.PSCredential -argumentlist $login,$pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="SQLAuthInvSqlCmd"></a> 使用 Invoke-Sqlcmd 的 SQL Server 驗證  
 **搭配使用 Invoke-Sqlcmd 與 SQL Server 驗證**  
  
1.  使用 **–Username** 參數指定登入識別碼，而 **–Password** 參數則可指定相關聯的密碼。  
  
### <a name="example-invoke-sqlcmd"></a>範例 (Invoke-Sqlcmd)  
 此範例使用 read-host Cmdlet 提示使用者輸入密碼，然後使用 SQL Server 驗證進行連接。  
  
```  
## Prompt the user for their password.  
$pwd = read-host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" –Username “MyLogin” –Password $pwd  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
 [SQL Server PowerShell 提供者](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Invoke-Sqlcmd 指令程式](../../powershell/invoke-sqlcmd-cmdlet.md)  
  
  
