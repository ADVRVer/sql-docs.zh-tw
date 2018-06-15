---
title: DROP SERVER ROLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: pdw, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP SERVER ROLE
- DROP_SERVER_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER ROLE, DROP
- DROP SERVER ROLE statement
ms.assetid: a2a1e6e6-e40c-4d6a-81be-d197b80bf226
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3f0d7ede0f8d714fcf90bf62d57b62acf220a4aa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "33066875"
---
# <a name="drop-server-role-transact-sql"></a>DROP SERVER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-pdw-md.md)]

  移除使用者定義伺服器角色。  
  
 使用者定義的伺服器角色是 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 新功能。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
DROP SERVER ROLE role_name  
```  
  
## <a name="arguments"></a>引數  
 *role_name*  
 指定要從伺服器卸除的使用者定義伺服器角色。  
  
## <a name="remarks"></a>Remarks  
 擁有安全性實體的使用者定義伺服器角色，不可以從伺服器卸除。 若要卸除一個擁有安全性實體的使用者定義伺服器角色，必須先轉移那些安全性實體的擁有權，或者刪除安全性實體。  
  
 含有成員的使用者定義伺服器角色，不可以卸除。 若要卸除具有成員的使用者定義伺服器角色，您必須先使用 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) 移除角色的成員。  
  
 固定伺服器角色無法移除。  
  
 您可以查詢 [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md) 目錄檢視，檢視角色成員資格的相關資訊。  
  
## <a name="permissions"></a>Permissions  
 需要伺服器角色的 CONTROL 權限或 ALTER ANY SERVER ROLE 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-to-drop-a-server-role"></a>A. 若要卸除伺服器角色  
 下列範例會卸除 `purchasing` 伺服器角色。  
  
```  
DROP SERVER ROLE purchasing;  
GO  
```  
  
### <a name="b-to-view-role-membership"></a>B. 若要檢視角色成員資格  
 若要檢視角色成員資格，請使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的**伺服器角色 (成員)** 頁面，或執行下列查詢：  
  
```  
SELECT SRM.role_principal_id, SP.name AS Role_Name,   
SRM.member_principal_id, SP2.name  AS Member_Name  
FROM sys.server_role_members AS SRM  
JOIN sys.server_principals AS SP  
    ON SRM.Role_principal_id = SP.principal_id  
JOIN sys.server_principals AS SP2   
    ON SRM.member_principal_id = SP2.principal_id  
ORDER BY  SP.name,  SP2.name  
```  
  
### <a name="c-to-view-role-membership"></a>C. 若要檢視角色成員資格  
 若要判斷伺服器角色是否擁有另一個伺服器角色，請執行下列查詢：  
  
```  
SELECT SP1.name AS RoleOwner, SP2.name AS Server_Role  
FROM sys.server_principals AS SP1  
JOIN sys.server_principals AS SP2  
    ON SP1.principal_id = SP2.owning_principal_id   
ORDER BY SP1.name ;  
```  
  
## <a name="see-also"></a>另請參閱  
 [ALTER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [DROP ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
