---
title: "sys.sql_logins (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 01/20/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sql_logins_TSQL
- sql_logins_TSQL
- sys.sql_logins
- sql_logins
dev_langs: TSQL
helpviewer_keywords: sys.sql_logins catalog view
ms.assetid: 0d9c5b09-86fe-40ff-baab-00b7c051402f
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 12dcc799255ebc44ed2b8d6401de80a98d83bcbb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="syssqllogins-transact-sql"></a>sys.sql_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  針對每一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入，各傳回一個資料列。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**\<繼承資料行 >**|--|繼承自**sys.server_principals**。|  
|**is_policy_checked**|**bit**|已經檢查密碼原則。|  
|**is_expiration_checked**|**bit**|已經檢查密碼逾期。|  
|**password_hash**|**varbinary(256)**|SQL 登入密碼的雜湊。 開頭為[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 預存密碼資訊會計算使用之 salt 的密碼 sha-512。|  
  
 如需這個檢視所繼承的資料行的清單，請參閱[sys.server_principals &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="remarks"></a>備註  
 若要檢視同時[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證登入和 Windows 驗證登入，請參閱[sys.server_principals &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 當自主資料庫使用者所啟用，不具有登入進行連接。 若要識別這些帳戶，請參閱[sys.database_principals &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入都可以查看他們自己的登入名稱和 sa 登入。 若要查看其他登入，則需要 ALTER ANY LOGIN 或該登入的權限。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [安全性目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [密碼原則](../../relational-databases/security/password-policy.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
