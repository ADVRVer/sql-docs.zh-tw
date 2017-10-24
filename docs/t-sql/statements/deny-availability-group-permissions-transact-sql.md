---
title: "拒絕可用性群組的權限 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], permissions
- permissions [SQL Server], availability group
- DENY statement, availability groups
- denying permissions, [SQL Server], availability groups
ms.assetid: bda60b36-a0b9-4c20-80c1-6a5cb1d638a5
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1d2e96c60c2811f0a0a87de3d50e3567cd8655cf
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="deny-availability-group-permissions-transact-sql"></a>拒絕可用性群組權限 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  拒絕的權限 Always On 可用性群組中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
DENY permission  [ ,...n ] ON AVAILABILITY GROUP :: availability_group_name  
        TO < server_principal >  [ ,...n ]  
    [ CASCADE ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
        SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey  
```  
  
## <a name="arguments"></a>引數  
 *權限*  
 指定可以拒絕的可用性群組權限。 如需權限清單，請參閱這個主題稍後的「備註」一節。  
  
 可用性群組上**::***availability_group_name*  
 指定要拒絕其權限的可用性群組。 範圍限定詞 (**::**) 是必要。  
  
 若要\<server_principal >  
 指定要拒絕其權限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。  
  
 *SQL_Server_login*  
 指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的名稱。  
  
 *SQL_Server_login_from_Windows_login*  
 指定從 Windows 登入建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入名稱。  
  
 *SQL_Server_login_from_certificate*  
 指定對應至憑證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入名稱。  
  
 *SQL_Server_login_from_AsymKey*  
 指定對應至非對稱金鑰的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入名稱。  
  
 CASCADE  
 指出目前受到拒絕的權限，也為這個主體曾授與此權限的其他主體所拒絕。  
  
 AS *SQL_Server_login*  
 指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]從中執行此查詢的主體衍生權限來拒絕權限的登入。  
  
## <a name="remarks"></a>備註  
 只有當目前資料庫是可以拒絕伺服器範圍的權限**主要**。  
  
 可用性群組的相關資訊會顯示在[sys.availability_groups &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)目錄檢視。 伺服器權限的資訊會顯示在[sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)目錄檢視，以及有關伺服器主體的資訊會顯示在[sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)目錄檢視。  
  
 可用性群組是伺服器層級的安全性實體。 下表所列的是可以拒絕之最特定且最有限的可用性群組權限，並列出利用隱含方式來併入這些權限的較通用權限。  
  
|可用性群組權限|可用性群組權限所隱含|伺服器權限所隱含|  
|-----------------------------------|----------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY AVAILABILITY GROUP|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 需要可用性群組的 CONTROL 權限或伺服器的 ALTER ANY AVAILABILTIY GROUP 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-denying-view-definition-permission-on-an-availability-group"></a>A. 拒絕可用性群組的 VIEW DEFINITION 權限  
 下列範例會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入 `VIEW DEFINITION` 拒絕可用性群組 `MyAg` 的 `ZArifin` 權限。  
  
```  
USE master;  
DENY VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-denying-take-ownership-permission-with-the-cascade-option"></a>B. 拒絕具有 CASCADE 的 TAKE OWNERSHIP 權限  
 下列範例會對具有 `TAKE OWNERSHIP` 選項之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者  `MyAg` 拒絕可用性群組 `PKomosinski` 的 `CASCADE` 權限。  
  
```  
USE master;  
DENY TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    CASCADE;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [撤銷可用性群組的權限 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)   
 [授與可用性群組的權限 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [sys.availability_groups &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性群組目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [權限 &#40;資料庫引擎&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

