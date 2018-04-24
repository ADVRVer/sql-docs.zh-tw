---
title: GRANT 伺服器權限 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- GRANT statement, servers
- permissions [SQL Server], servers
- servers [SQL Server], permissions
- granting permissions [SQL Server], servers
ms.assetid: 7e880a5a-3bdc-491f-a167-7a9ed338be7f
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3239f78d4e3114d652892e7de9ab3dfe1adb93e2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="grant-server-permissions-transact-sql"></a>GRANT 伺服器權限 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  授與伺服器的權限。 
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
GRANT permission [ ,...n ]   
    TO <grantee_principal> [ ,...n ] [ WITH GRANT OPTION ]  
    [ AS <grantor_principal> ]  
  
<grantee_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
  
<grantor_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
```  
  
## <a name="arguments"></a>引數  
 *permission*  
 指定可以授與的伺服器權限。 如需權限清單，請參閱這個主題稍後的「備註」一節。  
  
 TO \<grantee_principal> 指定要對其授與權限的主體。  
  
 AS \<grantor_principal> 指定主體，以讓執行這項查詢的主體可從該主體衍生授與權限的權力。  
  
 WITH GRANT OPTION  
 指出主體也有權授與指定權限給其他主體。  
  
 *SQL_Server_login*  
 指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。  
  
 *SQL_Server_login_mapped_to_Windows_login*  
 指定對應至 Windows 登入的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。  
  
 *SQL_Server_login_mapped_to_Windows_group*  
 指定對應至 Windows 群組的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。  
  
 *SQL_Server_login_mapped_to_certificate*  
 指定對應至憑證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。  
  
 *SQL_Server_login_mapped_to_asymmetric_key*  
 指定對應至非對稱金鑰的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。  
  
 *server_role*  
 指定使用者定義伺服器角色。  
  
## <a name="remarks"></a>Remarks  
 只有在目前資料庫是 master 的情況下，才能夠授與伺服器範圍的權限。  
  
 您可以在 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) 目錄檢視中檢視伺服器權限的資訊，而在 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) 目錄檢視中檢視伺服器主體的資訊。 您可以在 [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md) 目錄檢視中檢視伺服器角色成員資格的資訊。  
  
 伺服器是最高層級的權限階層。 下表所列的是可以授與之最特定且最有限的伺服器權限。  
  
|伺服器權限|伺服器權限所隱含|  
|-----------------------|----------------------------------|  
|ADMINISTER BULK OPERATIONS|CONTROL SERVER|  
|ALTER ANY AVAILABILITY GROUP<br /><br /> **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|CONTROL SERVER|  
|ALTER ANY CONNECTION|CONTROL SERVER|  
|ALTER ANY CREDENTIAL|CONTROL SERVER|  
|ALTER ANY DATABASE|CONTROL SERVER|  
|ALTER ANY ENDPOINT|CONTROL SERVER|  
|ALTER ANY EVENT NOTIFICATION|CONTROL SERVER|  
|ALTER ANY EVENT SESSION|CONTROL SERVER|  
|ALTER ANY LINKED SERVER|CONTROL SERVER|  
|ALTER ANY LOGIN|CONTROL SERVER|  
|ALTER ANY SERVER AUDIT|CONTROL SERVER|  
|ALTER ANY SERVER ROLE<br /><br /> **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|CONTROL SERVER|  
|ALTER RESOURCES|CONTROL SERVER|  
|ALTER SERVER STATE|CONTROL SERVER|  
|ALTER SETTINGS|CONTROL SERVER|  
|ALTER TRACE|CONTROL SERVER|  
|AUTHENTICATE SERVER|CONTROL SERVER|  
|CONNECT ANY DATABASE<br /><br /> **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|CONTROL SERVER|  
|CONNECT SQL|CONTROL SERVER|  
|CONTROL SERVER|CONTROL SERVER|  
|CREATE ANY DATABASE|ALTER ANY DATABASE|  
|CREATE AVAILABILITY GROUP<br /><br /> **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|ALTER ANY AVAILABILITY GROUP|  
|CREATE DDL EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|CREATE ENDPOINT|ALTER ANY ENDPOINT|  
|CREATE SERVER ROLE<br /><br /> **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|ALTER ANY SERVER ROLE|  
|CREATE TRACE EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|EXTERNAL ACCESS ASSEMBLY|CONTROL SERVER|  
|IMPERSONATE ANY LOGIN<br /><br /> **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|CONTROL SERVER|  
|SELECT ALL USER SECURABLES<br /><br /> **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|CONTROL SERVER|  
|SHUTDOWN|CONTROL SERVER|  
|UNSAFE ASSEMBLY|CONTROL SERVER|  
|VIEW ANY DATABASE|VIEW ANY DEFINITION|  
|VIEW ANY DEFINITION|CONTROL SERVER|  
|VIEW SERVER STATE|ALTER SERVER STATE|  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中已加入下列三個伺服器權限。  
  
 **CONNECT ANY DATABASE** 權限  
 將 **CONNECT ANY DATABASE** 授與登入，該登入必須連線到目前存在的所有資料庫，以及可能於日後建立的任何新資料庫。 不要在任何資料庫中授與超出連接的任何權限。 結合 **SELECT ALL USER SECURABLES** 或 **VIEW SERVER STATE**，以讓稽核程序檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的所有資料或所有資料庫狀態。  
  
 **IMPERSONATE ANY LOGIN** 權限  
 授與此權限時，可讓中間層程序在連接到資料庫時模擬連接的用戶端帳戶。 拒絕此權限時，高權限登入可能遭到封鎖，而無法模擬其他登入。 例如，具有 **CONTROL SERVER** 權限的登入可能遭到封鎖，而無法模擬其他登入。  
  
 **SELECT ALL USER SECURABLES** 權限  
 授與此權限時，像是稽核者這類登入就可以檢視使用者可連接之所有資料庫中的資料。 拒絕此權限時，可防止存取不在 **sys** 結構描述中的物件。  
  
## <a name="permissions"></a>Permissions  
 同意授權者 (或是指定了 AS 選項的主體) 必須具有指定了 GRANT OPTION 的權限本身，或是具有隱含目前正在授與權限的更高權限。 系統管理員 (sysadmin) 固定伺服器角色的成員也能夠授與任何權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-granting-a-permission-to-a-login"></a>A. 授與權限給登入  
 下列範例會將 `CONTROL SERVER` 權限授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入 `TerryEminhizer`。  
  
```  
USE master;  
GRANT CONTROL SERVER TO TerryEminhizer;  
GO  
```  
  
### <a name="b-granting-a-permission-that-has-grant-permission"></a>B. 授與具有 GRANT 權限的權限  
 下列範例會將 `ALTER ANY EVENT NOTIFICATION` 授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入 `JanethEsteves`，而這項登入具有對將該權限授與其他登入的權限。  
  
```  
USE master;  
GRANT ALTER ANY EVENT NOTIFICATION TO JanethEsteves WITH GRANT OPTION;  
GO  
```  
  
### <a name="c-granting-a-permission-to-a-server-role"></a>C. 授與權限給伺服器角色  
 下列範例會建立兩個名稱為 `ITDevAdmin` 和 `ITDevelopers` 的伺服器角色。 它會將 `ALTER ANY DATABASE` 權限授與 `ITDevAdmin` 使用者定義的伺服器角色，包括 `WITH GRANT` 選項，讓 `ITDevAdmin` 伺服器角色可以重新指派 `ALTER ANY DATABASE` 權限。 此範例接著會授權 `ITDevelopers` 使用 `ALTER ANY DATABASE` 伺服器角色的 `ITDevAdmin` 權限。  
  
```  
USE master;  
CREATE SERVER ROLE ITDevAdmin ;  
CREATE SERVER ROLE ITDevelopers ;  
GRANT ALTER ANY DATABASE TO ITDevAdmin WITH GRANT OPTION ;  
GRANT ALTER ANY DATABASE TO ITDevelopers AS ITDevAdmin ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [DENY 伺服器權限 &#40;Transact-SQL&#41;](../../t-sql/statements/deny-server-permissions-transact-sql.md)   
 [REVOKE 伺服器權限 &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-server-permissions-transact-sql.md)   
 [權限階層 &#40;Database Engine&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [權限 &#40;資料庫引擎&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fn_my_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  

