---
title: "更改伺服器稽核規格 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER SERVER AUDIT SPECIFICATION
- ALTER_SERVER_AUDIT_SPECIFICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
- ALTER SERVER AUDIT SPECIFICATION statement
ms.assetid: 9cac288b-940e-4c16-88d6-de06aeed2b47
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f24ae377451dff8e95bb20668d9cedd6c64b27cc
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="alter-server-audit-specification-transact-sql"></a>ALTER SERVER AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit 功能改變伺服器稽核規格物件。 如需詳細資訊，請參閱 [SQL Server Audit &#40;Database Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
ALTER SERVER AUDIT SPECIFICATION audit_specification_name  
{  
    [ FOR SERVER AUDIT audit_name ]  
    [ { { ADD | DROP } ( audit_action_group_name )  
      } [, ...n] ]  
    [ WITH ( STATE = { ON | OFF } ) ]  
}  
[ ; ]  
```  
  
## <a name="arguments"></a>引數  
 *audit_specification_name*  
 稽核規格的名稱。  
  
 *audit_name*  
 套用此規格的稽核名稱。  
  
 *audit_action_group_name*  
 伺服器層級之可稽核動作的群組名稱。 如需稽核動作群組的清單，請參閱[SQL Server Audit 動作群組和動作](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md)。  
  
 與**(**狀態 **=**  {ON |關閉} **)**  
 啟用或停用從這個稽核規格收集而來之記錄的稽核。  
  
## <a name="remarks"></a>備註  
 您必須設定稽核規格的狀態為 OFF 選項，來進行稽核規格變更。 如果在設定 STATE=OFF 以外的任何選項時啟用稽核，而且執行 ALTER SERVER AUDIT SPECIFICATION，您將會收到錯誤訊息。  
  
## <a name="permissions"></a>Permissions  
 具有 ALTER ANY SERVER AUDIT 權限的使用者可以改變伺服器稽核規格，並將其繫結至任何稽核。  
  
 一旦建立伺服器稽核規格之後，就可以使用具有 CONTROL SERVER 或 ALTER ANY SERVER AUDIT 權限的主體、系統管理員 (sysadmin) 帳戶或具有此稽核之明確存取權的主體來加以檢視。  
  
## <a name="examples"></a>範例  
 下列範例會建立一個稱為 `HIPPA_Audit_Specification` 的伺服器稽核規格。 它會捨棄失敗的登入的稽核動作群組，然後加入 Database Object Access 的稽核動作群組[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]稽核呼叫`HIPPA_Audit`。  
  
```  
ALTER SERVER AUDIT SPECIFICATION HIPPA_Audit_Specification  
FOR SERVER AUDIT HIPPA_Audit  
    DROP (FAILED_LOGIN_GROUP)  
    ADD (DATABASE_OBJECT_ACCESS_GROUP);  
GO  
```  
  
 如需有關如何建立稽核的完整範例，請參閱[SQL Server Audit &#40; Database engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)。  
  

## <a name="see-also"></a>另請參閱  
 [建立伺服器稽核 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [建立伺服器稽核規格 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [建立資料庫稽核規格 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [卸除資料庫稽核規格 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;TRANSACT-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [建立伺服器稽核與伺服器稽核規格](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  

