---
title: "授與 Service Broker 權限 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- granting permissions [SQL Server], Service Broker
- routes [Service Broker], permissions
- Service Broker, permissions
- GRANT statement, Service Broker
- remote service bindings [Service Broker], permissions
- message types [Service Broker], permissions
- contracts [Service Broker], permissions
ms.assetid: c5579976-97c4-4123-be0c-d0b98a9e38fb
caps.latest.revision: "17"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0383e0b5446537b77e02ce4b8e4d3e54c850bdd1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="grant-service-broker-permissions-transact-sql"></a>GRANT Service Broker 權限 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  授與 Service Broker 合約、訊息類型、遠端繫結、路由或服務的權限。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
GRANT permission  [ ,...n ] ON  
    {    
              [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
    }  
    TO database_principal [ ,...n ]   
    [ WITH GRANT OPTION ]  
        [ AS granting_principal ]  
```  
  
## <a name="arguments"></a>引數  
 *permission*  
 指定可以授與的 Service Broker 安全性實體權限。  如下所列。  
  
 合約 **:: * * * contract_name*  
 指定正在授與權限的合約。 範圍限定詞"::"是必要。  
  
 MESSAGE TYPE **::***message_type_name*  
 指定正在授與權限的訊息類型。 需要範圍限定詞 "::"。  
  
 遠端服務繫結 **:: * * * remote_binding_name*  
 指定正在授與權限的遠端服務繫結。 需要範圍限定詞 "::"。  
  
 ROUTE **::***route_name*  
 指定正在授與權限的路由。 需要範圍限定詞 "::"。  
  
 SERVICE **::***service_name*  
 指定正在授與權限的服務。 需要範圍限定詞 "::"。  
  
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
  
 *granting_principal*  
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
  
## <a name="service-broker-contracts"></a>Service Broker 合約  
 Service Broker 合約是在權限階層中，身為其父系之資料庫所包含的一個資料庫層級安全性實體。 下面所列的是可以授與之最特定且最有限的 Service Broker 合約權限，另外還有以隱含方式包含它們的較通用權限。  
  
|Service Broker 合約權限|Service Broker 合約權限所隱含|資料庫權限所隱含|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Service Broker 訊息類型  
 Service Broker 訊息類型是在權限階層中，身為其父系之資料庫所包含的一個資料庫層級安全性實體。 下面所列的是可以授與之最特定且最有限的 Service Broker 訊息類型權限，另外還有以隱含方式包含它們的較通用權限。  
  
|Service Broker 訊息類型權限|Service Broker 訊息類型權限所隱含|資料庫權限所隱含|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Service Broker 遠端服務繫結  
 Service Broker 遠端服務繫結是在權限階層中，身為其父系之資料庫所包含的一個資料庫層級安全性實體。 下面所列的是可以授與之最特定且最有限的 Service Broker 遠端服務繫結權限，另外還有以隱含方式包含它們的較通用權限。  
  
|Service Broker 遠端服務繫結權限|Service Broker 遠端服務繫結權限所隱含|資料庫權限所隱含|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Service Broker 路由  
 Service Broker 路由是在權限階層中，身為其父系之資料庫所包含的一個資料庫層級安全性實體。 下面所列的是可以授與之最特定且最有限的 Service Broker 路由權限，另外還有以隱含方式包含它們的較通用權限。  
  
|Service Broker 路由權限|Service Broker 路由權限所隱含|資料庫權限所隱含|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Service Broker 服務  
 Service Broker 服務是在權限階層中，身為其父系之資料庫所包含的一個資料庫層級安全性實體。 下面所列的是可以授與之最特定且最有限的 Service Broker 服務權限，另外還有以隱含方式包含它們的較通用權限。  
  
|Service Broker 服務權限|Service Broker 服務權限所隱含|資料庫權限所隱含|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
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
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [權限 &#40;資料庫引擎&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
