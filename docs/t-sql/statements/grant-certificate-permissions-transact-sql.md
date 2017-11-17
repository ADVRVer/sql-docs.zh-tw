---
title: "GRANT 憑證權限 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], certificates
- certificates [SQL Server], permissions
- permissions [SQL Server], certificates
- GRANT statement, certificates
ms.assetid: 77270245-a24b-4a20-b481-e6a5ea05b499
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06cd8f6b6b9e6a05326bad54319961a2120b979d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="grant-certificate-permissions-transact-sql"></a>GRANT 憑證權限 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中授與憑證的權限。 
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```
GRANT permission  [ ,...n ]    
    ON CERTIFICATE :: certificate_name   
    TO principal [ ,...n ] [ WITH GRANT OPTION ]   
    [ AS granting_principal ]   
```  
  
## <a name="arguments"></a>引數  
 *權限*  
 指定可以授與的憑證權限。 如下所列。  
  
 ON 憑證**::***certificate_name*  
 指定正在授與權限的憑證。 需要範圍限定詞 "::"。  
  
 *database_principal*  
 指定要對其授與權限的主體。 它有下列幾種：  
  
-   資料庫使用者  
-   資料庫角色  
-   應用程式角色  
-   對應至 Windows 登入的資料庫使用者  
-   對應至 Windows 群組的資料庫使用者  
-   對應至憑證的資料庫使用者  
-   對應至非對稱金鑰的資料庫使用者  
-   未對應至伺服器主體的資料庫使用者  
  
GRANT OPTION  
 指出主體也有權授與指定權限給其他主體。  
  
AS *granting_principal*  
 指定主體，執行這項查詢的主體就是從這個主體衍生權限來授與權限。 它有下列幾種：  
  
-   資料庫使用者  
-   資料庫角色  
-   應用程式角色  
-   對應至 Windows 登入的資料庫使用者  
-   對應至 Windows 群組的資料庫使用者  
-   對應至憑證的資料庫使用者  
-   對應至非對稱金鑰的資料庫使用者  
-   未對應至伺服器主體的資料庫使用者  
  
## <a name="remarks"></a>備註  
 憑證是一個由資料庫所包含的資料庫層級安全性實體，在權限階層中，此資料庫為該安全性實體的父系。 下面所列的是可以授與之最特定且最有限的憑證權限，並列出利用隱含方式來併入這些權限的較通用權限。  
  
|憑證權限|憑證權限所隱含|資料庫權限所隱含|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CERTIFICATE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 同意授權者 (或是指定了 AS 選項的主體) 必須具有指定了 GRANT OPTION 的權限本身，或是具有隱含目前正在授與權限的更高權限。  
  
 如果是使用 AS 選項，就必須套用這些額外的需求。  
  
|AS *granting_principal*|其他必要的權限|  
|------------------------------|------------------------------------|  
|資料庫使用者|中的成員資格使用者的 IMPERSONATE 權限**db_securityadmin**固定的資料庫角色、 成員資格**db_owner**固定資料庫角色或中的成員資格**sysadmin**固定的伺服器角色。|  
|對應至 Windows 登入的資料庫使用者|中的成員資格使用者的 IMPERSONATE 權限**db_securityadmin**固定的資料庫角色、 成員資格**db_owner**固定資料庫角色或中的成員資格**sysadmin**固定的伺服器角色。|  
|對應至 Windows 群組的資料庫使用者|在 Windows 群組中的成員資格的成員資格**db_securityadmin**固定的資料庫角色、 成員資格**db_owner**固定資料庫角色或中的成員資格**sysadmin**固定的伺服器角色。|  
|對應至憑證的資料庫使用者|中的成員資格**db_securityadmin**固定的資料庫角色、 成員資格**db_owner**固定資料庫角色或中的成員資格**sysadmin**固定的伺服器角色。|  
|對應至非對稱金鑰的資料庫使用者|中的成員資格**db_securityadmin**固定的資料庫角色、 成員資格**db_owner**固定資料庫角色或中的成員資格**sysadmin**固定的伺服器角色。|  
|未對應至任何伺服器主體的資料庫使用者|中的成員資格使用者的 IMPERSONATE 權限**db_securityadmin**固定的資料庫角色、 成員資格**db_owner**固定資料庫角色或中的成員資格**sysadmin**固定的伺服器角色。|  
|資料庫角色|ALTER 權限的角色中的成員資格**db_securityadmin**固定的資料庫角色、 成員資格**db_owner**固定資料庫角色或中的成員資格**sysadmin**固定的伺服器角色。|  
|應用程式角色|ALTER 權限的角色中的成員資格**db_securityadmin**固定的資料庫角色、 成員資格**db_owner**固定資料庫角色或中的成員資格**sysadmin**固定的伺服器角色。|  
  
 物件擁有者可以授與他們所擁有之物件的權限。 具有安全性實體之 CONTROL 權限的主體可以授與該安全性實體的權限。  
  
 被授與者的 CONTROL SERVER 權限，例如的成員**sysadmin**固定的伺服器角色可授與任何權限的任何伺服器安全性實體。 被授與者的 CONTROL 權限的資料庫，例如的成員**db_owner**固定的資料庫角色可授與任何權限的任何安全性實體，在資料庫中。 結構描述之 CONTROL 權限的被授與者，可以授與結構描述中任何物件的任何權限。  
  
## <a name="see-also"></a>另請參閱  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [權限 &#40;資料庫引擎&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [建立應用程式角色 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

