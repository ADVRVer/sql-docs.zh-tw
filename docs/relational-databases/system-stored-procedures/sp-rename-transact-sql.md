---
title: "sp_rename (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_rename_TSQL
- sp_rename
dev_langs: TSQL
helpviewer_keywords:
- renaming indexes
- renaming columns
- sp_rename
- renaming tables
ms.assetid: bc3548f0-143f-404e-a2e9-0a15960fc8ed
caps.latest.revision: "54"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: eb402624e8b25f43a1969a91df85cfe5fa85d9af
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="sprename-transact-sql"></a>sp_rename (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  變更目前資料庫中之使用者建立物件的名稱。 這個物件可以是資料表、 索引、 資料行別名資料類型，或[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR) 使用者定義型別。  
  
> [!CAUTION]  
>  變更物件名稱的任何部分，可能破壞指令碼和預存程序。 我們建議您不要使用陳述式來重新命名預存程序、觸發程序、使用者定義函數或檢視；相反地，請卸除物件，再利用新名稱來重新建立它。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_rename [ @objname = ] 'object_name' , [ @newname = ] 'new_name'   
    [ , [ @objtype = ] 'object_type' ]   
```  
  
## <a name="arguments"></a>引數  
 [ @objname =] '*object_name*'  
 這是使用者物件或資料類型目前的完整或非完整名稱。 如果要重新命名的物件是在資料表中，資料行*object_name*格式必須為*table.column*或*schema.table.column*。 如果要重新命名的物件是索引， *object_name*格式必須為*table.index*或*schema.table.index*。 如果要重新命名的物件是條件約束， *object_name*格式必須為*schema.constraint*。  
  
 只有在指定限定物件時，才需要引號。 如果提供其中包括資料庫名稱的完整名稱，資料庫名稱就必須是目前資料庫的名稱。 *object_name*是**nvarchar(776)**，沒有預設值。  
  
 [ @newname =] '*new_name*'  
 這是指定物件的新名稱。 *new_name*必須是單部分名稱，且必須遵照識別碼的規則。 *newname*是**sysname**，沒有預設值。  
  
> [!NOTE]  
>  觸發程序名稱的開頭不能是 # 或 ##。  
  
 [ @objtype =] '*object_type*'  
 這是要重新命名的物件類型。 *object_type*是**varchar(13)**，預設值是 NULL，而且可以是下列值之一。  
  
|值|Description|  
|-----------|-----------------|  
|COLUMN|要重新命名的資料行。|  
|DATABASE|使用者定義資料庫。 當重新命名資料庫時，需要這個物件類型。|  
|INDEX|使用者自訂索引。 重新命名具有統計資料的索引時，也會自動重新命名統計資料。|  
|OBJECT|中的追蹤類型項目[sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)。 例如，您可以利用 OBJECT 來重新命名物件，其中包括條件約束 (CHECK、FOREIGN KEY、PRIMARY/UNIQUE KEY)、使用者資料表和規則。|  
|STATISTICS|**適用於**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]透過[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]和[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。<br /><br /> 使用者明確建立的統計資料，或使用索引隱含建立的統計資料。 重新命名索引的統計資料時，也會自動重新命名索引。|  
|USERDATATYPE|A [CLR 使用者定義型別](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)加入執行[CREATE TYPE](../../t-sql/statements/create-type-transact-sql.md)或[sp_addtype](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md)。|  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或非零數字 (失敗)  
  
## <a name="remarks"></a>備註  
 您只能變更目前資料庫中的物件或資料類型的名稱。 您無法改變大部分系統資料類型和系統物件的名稱。  
  
 每當重新命名 PRIMARY KEY 或 UNIQUE 條件約束時，sp_rename 都會自動重新命名相關聯的索引。 如果是重新命名的索引繫結於 PRIMARY KEY 條件約束，sp_rename 也會自動重新命名 PRIMARY KEY 條件約束。  
  
 您可以利用 sp_rename 來重新命名主要和次要 XML 索引。  
  
 重新命名預存程序、 函數、 檢視或觸發程序並不會變更對應的物件名稱中的 definition 資料行名稱[sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)目錄檢視。 因此，我們建議您不要利用 sp_rename 來重新命名這些物件類型。 相反地，請卸除物件，再利用它的新名稱來重新建立物件。  
  
 重新命名資料表或資料行之類的物件，不會自動重新命名指向這個物件的參考。 您必須手動修改任何參考重新命名之物件的物件。 例如，如果您重新命名資料表資料行，且有觸發程序參考這個資料行，您必須修改觸發程序來反映新的資料行名稱。 使用[sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)清單相依性物件上再重新命名它。  
  
## <a name="permissions"></a>Permissions  
 若要重新命名物件、資料行和索引，需要物件的 ALTER 權限。 若要重新命名使用者類型，需要這個類型的 CONTROL 權限。 若要重新命名資料庫，需要系統管理員 (sysadmin) 或資料庫建立者 (dbcreator) 固定伺服器角色中的成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-renaming-a-table"></a>A. 重新命名資料表  
 下列範例會將 `SalesTerritory` 資料表重新命名為 `SalesTerr` 結構描述中的 `Sales` 。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
GO  
```  
  
### <a name="b-renaming-a-column"></a>B. 重新命名資料行  
 下列範例會重新命名`TerritoryID`中的資料行`SalesTerritory`資料表`TerrID`。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
GO  
```  
  
### <a name="c-renaming-an-index"></a>C. 重新命名索引  
 下列範例會將 `IX_ProductVendor_VendorID` 索引重新命名成 `IX_VendorID`。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename N'Purchasing.ProductVendor.IX_ProductVendor_VendorID', N'IX_VendorID', N'INDEX';  
GO  
```  
  
### <a name="d-renaming-an-alias-data-type"></a>D. 重新命名別名資料類型  
 下列範例會將 `Phone` 別名資料類型重新命名成 `Telephone`。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename N'Phone', N'Telephone', N'USERDATATYPE';  
GO  
```  
  
### <a name="e-renaming-constraints"></a>E. 重新命名條件約束  
 下列範例會重新命名 PRIMARY KEY 條件約束、CHECK 條件約束和 FOREIGN KEY 條件約束。 重新命名條件約束時，您必須指定條件約束所屬的結構描述。  
  
```  
USE AdventureWorks2012;   
GO  
-- Return the current Primary Key, Foreign Key and Check constraints for the Employee table.  
SELECT name, SCHEMA_NAME(schema_id) AS schema_name, type_desc  
FROM sys.objects  
WHERE parent_object_id = (OBJECT_ID('HumanResources.Employee'))   
AND type IN ('C','F', 'PK');   
GO  
  
-- Rename the primary key constraint.  
sp_rename 'HumanResources.PK_Employee_BusinessEntityID', 'PK_EmployeeID';  
GO  
  
-- Rename a check constraint.  
sp_rename 'HumanResources.CK_Employee_BirthDate', 'CK_BirthDate';  
GO  
  
-- Rename a foreign key constraint.  
sp_rename 'HumanResources.FK_Employee_Person_BusinessEntityID', 'FK_EmployeeID';  
  
-- Return the current Primary Key, Foreign Key and Check constraints for the Employee table.  
SELECT name, SCHEMA_NAME(schema_id) AS schema_name, type_desc  
FROM sys.objects  
WHERE parent_object_id = (OBJECT_ID('HumanResources.Employee'))   
AND type IN ('C','F', 'PK');  
  
```  
  
```  
  
name                                  schema_name        type_desc  
------------------------------------- ------------------ ----------------------  
FK_Employee_Person_BusinessEntityID   HumanResources     FOREIGN_KEY_CONSTRAINT  
PK_Employee_BusinessEntityID          HumanResources     PRIMARY_KEY_CONSTRAINT  
CK_Employee_BirthDate                 HumanResources     CHECK_CONSTRAINT  
CK_Employee_MaritalStatus             HumanResources     CHECK_CONSTRAINT  
CK_Employee_HireDate                  HumanResources     CHECK_CONSTRAINT  
CK_Employee_Gender                    HumanResources     CHECK_CONSTRAINT  
CK_Employee_VacationHours             HumanResources     CHECK_CONSTRAINT  
CK_Employee_SickLeaveHours            HumanResources     CHECK_CONSTRAINT  
  
(7 row(s) affected)  
  
name                                  schema_name        type_desc  
------------------------------------- ------------------ ----------------------  
FK_Employee_ID                        HumanResources     FOREIGN_KEY_CONSTRAINT  
PK_Employee_ID                        HumanResources     PRIMARY_KEY_CONSTRAINT  
CK_BirthDate                          HumanResources     CHECK_CONSTRAINT  
CK_Employee_MaritalStatus             HumanResources     CHECK_CONSTRAINT  
CK_Employee_HireDate                  HumanResources     CHECK_CONSTRAINT  
CK_Employee_Gender                    HumanResources     CHECK_CONSTRAINT  
CK_Employee_VacationHours             HumanResources     CHECK_CONSTRAINT  
CK_Employee_SickLeaveHours            HumanResources     CHECK_CONSTRAINT  
  
(7 row(s) affected)  
  
```  
  
### <a name="f-renaming-statistics"></a>F. 重新命名統計資料  
 下列範例會建立名為 contactMail1 統計資料物件，然後會重新命名統計資料為 NewContact 使用 sp_rename。 當重新命名統計資料時，必須以 schema.table.statistics_name 格式指定物件。  
  
```  
CREATE STATISTICS ContactMail1  
    ON Person.Person (BusinessEntityID, EmailPromotion)  
    WITH SAMPLE 5 PERCENT;  
  
sp_rename 'Person.Person.ContactMail1', 'NewContact','Statistics';  
  
```  
  
## <a name="see-also"></a>請參閱  
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Database Engine 預存程序 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
