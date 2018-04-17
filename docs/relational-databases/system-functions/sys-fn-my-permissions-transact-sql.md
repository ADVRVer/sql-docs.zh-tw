---
title: sys.fn_my_permissions (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fn_my_permissions_TSQL
- fn_my_permissions_TSQL
- sys.fn_my_permissions
- fn_my_permissions
dev_langs:
- TSQL
helpviewer_keywords:
- fn_my_permissions function
- sys.fn_my_permissions function
ms.assetid: 30f97f00-03d8-443a-9de9-9ec420b7699b
caps.latest.revision: 21
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7a650563bbfce5296e6a86a7abcb5fa712417aec
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sysfnmypermissions-transact-sql"></a>sys.fn_my_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回有效授與安全性實體上主體的權限清單。 相關的函數是[HAS_PERMS_BY_NAME](../../t-sql/functions/has-perms-by-name-transact-sql.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
fn_my_permissions ( securable , 'securable_class' )  
```  
  
## <a name="arguments"></a>引數  
 *securable*  
 這是安全性實體的名稱。 如果安全性實體是伺服器或資料庫，這個值應該設為 NULL。 *securable* 為 **sysname** 類型的純量運算式。 *安全性實體*可以是多部分名稱。  
  
 '*securable_class*'  
 這是列出權限之安全性實體的類別名稱。 *securable_class*是**sysname**。 *securable_class*必須是下列其中之一： 應用程式角色、 組件、 非對稱金鑰、 憑證、 合約、 資料庫、 ENDPOINT、 FULLTEXT CATALOG、 登入、 訊息類型、 物件、 REMOTE SERVICE BINDING、 角色、 路由、 結構描述、 伺服器、 服務對稱金鑰、 類型、 使用者、 XML 結構描述集合。  
  
## <a name="columns-returned"></a>傳回的資料行  
 下表列出的資料行， **fn_my_permissions**傳回。 傳回的每個資料列都會描述安全性實體之目前安全性內容所持有的權限。 如果查詢失敗，則傳回 NULL。  
  
|資料行名稱|類型|Description|  
|-----------------|----------|-----------------|  
|entity_name|**sysname**|有效授與列出權限的安全性實體名稱。|  
|subentity_name|**sysname**|如果安全性實體有資料行，則為資料行名稱，否則為 NULL。|  
|permission_name|**nvarchar**|權限的名稱。|  
  
## <a name="remarks"></a>備註  
 這個資料表值函式會傳回指定安全性實體之呼叫主體所持有的有效權限清單。 有效權限為下列項目之一：  
  
-   直接授與主體的權限，且不被拒絕。  
  
-   由主體保留的較高層級權限所隱含的權限，且不被拒絕。  
  
-   授與角色或群組的權限，主體為其成員之一，且不被拒絕。  
  
-   角色或群組所保留的權限，主體為其成員之一，且不被拒絕。  
  
 權限評估一律在呼叫端的安全性內容中執行。 若要決定另一個主體是否具有有效權限，呼叫端對該主體必須具有 IMPERSONATE 權限。  
  
 如果是結構描述層級實體，則接受一、二或三部分非 Null 名稱。 資料庫層級實體的一段式名稱則接受 null 值則表示 「*目前資料庫*"。 如果是伺服器本身，則 Null 值 (表示「目前伺服器」) 是必要的。 **fn_my_permissions**無法檢查連結的伺服器上的權限。  
  
 下列查詢將傳回內建安全性實體類別的清單：  
  
```  
SELECT DISTINCT class_desc FROM fn_builtin_permissions(default)  
    ORDER BY class_desc;  
GO  
```  
  
 如果預設提供的值為*安全*或*securable_class*，值會被解譯為 NULL。  
  
## <a name="examples"></a>範例  
  
### <a name="a-listing-effective-permissions-on-the-server"></a>A. 列出伺服器的有效權限  
 下列範例會傳回伺服器呼叫端的有效權限清單。  
  
```  
SELECT * FROM fn_my_permissions(NULL, 'SERVER');  
GO  
```  
  
### <a name="b-listing-effective-permissions-on-the-database"></a>B. 列出資料庫的有效權限  
 下列範例會傳回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫呼叫端的有效權限清單。  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions (NULL, 'DATABASE');  
GO  
```  
  
### <a name="c-listing-effective-permissions-on-a-view"></a>C. 列出檢視表的有效權限  
 下列範例會傳回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫之 `vIndividualCustomer` 結構描述中 `Sales` 檢視呼叫端的有效權限清單。  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('Sales.vIndividualCustomer', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;   
GO   
```  
  
### <a name="d-listing-effective-permissions-of-another-user"></a>D. 列出其他使用者的有效權限  
 下列範例會傳回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫之 `Wanida` 結構描述中 `Employee` 資料表資料庫使用者 `HumanResources` 的有效權限清單。 呼叫端需要使用者 `Wanida` 的 IMPERSONATE 權限。  
  
```  
EXECUTE AS USER = 'Wanida';  
SELECT * FROM fn_my_permissions('HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
### <a name="e-listing-effective-permissions-on-a-certificate"></a>E. 列出憑證的有效權限  
 下列範例會傳回目前資料庫中憑證名稱為 `Shipping47` 之呼叫端的有效權限清單。  
  
```  
SELECT * FROM fn_my_permissions('Shipping47', 'CERTIFICATE');  
GO  
```  
  
### <a name="f-listing-effective-permissions-on-an-xml-schema-collection"></a>F. 列出 XML 結構描述集合的有效權限  
 下列範例會傳回名為 XML 結構描述集合上的呼叫端的有效權限清單`ProductDescriptionSchemaCollection`中[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]資料庫。  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('ProductDescriptionSchemaCollection',  
    'XML SCHEMA COLLECTION');  
GO  
```  
  
### <a name="g-listing-effective-permissions-on-a-database-user"></a>G. 列出資料庫使用者的有效權限  
 下列範例會傳回目前資料庫中使用者名稱為 `MalikAr` 之呼叫端的有效權限清單。  
  
```  
SELECT * FROM fn_my_permissions('MalikAr', 'USER');  
GO  
```  
  
### <a name="h-listing-effective-permissions-of-another-login"></a>H. 列出其他登入的有效權限  
 下列範例會傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫之 `WanidaBenshoof` 結構描述中 `Employee` 資料表之 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 登入 `HumanResources` 的有效權限清單。 呼叫端需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入 `WanidaBenshoof` 的 IMPERSONATE 權限。  
  
```  
EXECUTE AS LOGIN = 'WanidaBenshoof';  
SELECT * FROM fn_my_permissions('AdventureWorks2012.HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [安全性函數 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [權限 &#40;資料庫引擎&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [安全性實體](../../relational-databases/security/securables.md)   
 [權限階層 &#40;Database Engine&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [安全性目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  
