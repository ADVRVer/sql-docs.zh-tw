---
title: "卸除資料表 (TRANSACT-SQL) |Microsoft 文件"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_TABLE_TSQL
- DROP TABLE
dev_langs:
- TSQL
helpviewer_keywords:
- removing indexes
- table removal [SQL Server]
- deleting indexes
- dropping data
- deleting tables
- dropping indexes
- removing constraints
- removing permissions
- DROP TABLE statement
- removing tables
- deleting triggers
- removing data
- dropping tables
- deleting permissions
- dropping triggers
- deleting constraints
- removing triggers
- deleting data
- dropping constraints
- dropping permissions
ms.assetid: 0b6f2b6f-3aa3-4767-943f-43df3c3c5cfd
caps.latest.revision: 61
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 22fa2a1da83dfef0743c089256fcd1e18af9b54c
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="drop-table-transact-sql"></a>DROP TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  移除一個或多個資料表定義及這些資料表的所有資料、索引、觸發程序、條件約束和權限規格。 任何檢視或預存程序參考已卸除的資料表必須先明確卸除使用[DROP VIEW](../../t-sql/statements/drop-view-transact-sql.md)或[DROP PROCEDURE](../../t-sql/statements/drop-procedure-transact-sql.md)。 若要報告的相依性的資料表上，使用[sys.dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP TABLE [ IF EXISTS ] [ database_name . [ schema_name ] . | schema_name . ]  
table_name [ ,...n ]  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP TABLE [ database_name . [ schema_name ] . | schema_name . ] table_name   
[;]  
```  
  
## <a name="arguments"></a>引數  
 *database_name*  
 這是建立資料表的資料庫名稱。  
  
 當 database_name 是目前的資料庫或 database_name 是 tempdb，而且 object_name 開頭為 # 時，Windows Azure SQL Database 支援三部分名稱格式 database_name.[schema_name].object_name。 Windows Azure SQL Database 不支援四部分名稱。  
  
 *如果存在*  
 **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。  
  
 只有當它已經存在有條件地卸除資料表。  
  
 *schema_name*  
 這是資料表所屬的結構描述名稱。  
  
 *table_name*  
 這是要移除的資料表名稱。  
  
## <a name="remarks"></a>備註  
 您無法利用 DROP TABLE 來卸除 FOREIGN KEY 條件約束所參考的資料表。 您必須先卸除參考 FOREIGN KEY 條件約束或參考資料表。 如果參考資料表和持有要卸除的主索引鍵之資料表在相同的 DROP TABLE 陳述式中，就必須先列出參考資料表。  
  
 您可以在任何資料庫中卸除多份資料表。 如果卸除的資料表參考另一份也要卸除的資料表之主索引鍵，含有外部索引鍵的參考資料表必須列在持有被參考的主索引鍵之資料表前面。  
  
 當卸除資料表時，資料表的規則或預設值會失去它們的繫結，資料表的任何相關條件約束或觸發程序也都會自動卸除。 如果重新建立資料表，您必須重新繫結適當的規則和預設值、重新建立任何觸發程序，以及加入所有必要的條件約束。  
  
 如果您可以使用 DELETE 刪除資料表中的所有資料列*tablename*或使用 TRUNCATE TABLE 陳述式，資料表存在，直到卸除它。  
  
 使用超出 128 個範圍的大型資料表和索引會分成邏輯和實體這兩個分開的階段來卸除。 在邏輯階段中，資料表所用的現有配置單位會標示成取消配置和鎖定，直到認可交易為止。 在實體階段中，會以批次方式來實際卸除標示成取消配置的 IAM 頁面。  
  
 如果卸除的資料表包含具有 FILESTREAM 屬性的 VARBINARY(MAX) 資料行，則儲存在檔案系統中的任何資料都不會遭到移除。  
  
> [!IMPORTANT]  
>  DROP TABLE 和 CREATE TABLE 不得在相同批次的相同資料表上執行。 否則，系統可能會發生非預期的錯誤。  
  
## <a name="permissions"></a>Permissions  
 需要資料表所屬結構描述的 ALTER 權限、資料表的 CONTROL 權限，或 **db_ddladmin** 固定資料庫角色成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-dropping-a-table-in-the-current-database"></a>A. 卸除目前資料庫中的資料表  
 下列範例會從目前資料庫移除 `ProductVendor1` 資料表及其資料和索引。  
  
```  
DROP TABLE ProductVendor1 ;  
```  
  
### <a name="b-dropping-a-table-in-another-database"></a>B. 卸除另一個資料庫中的資料表  
 下列範例會卸除 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中的 `SalesPerson2` 資料表。 您可以從伺服器執行個體的任何資料庫中執行這個範例。  
  
```  
DROP TABLE AdventureWorks2012.dbo.SalesPerson2 ;  
```  
  
### <a name="c-dropping-a-temporary-table"></a>C. 卸除暫存資料表  
 下列範例會建立一份暫存資料表、測試它是否存在、卸除它，再重新測試它是否存在。 此範例不使用**IF EXISTS**語法可從[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]。  
  
```  
CREATE TABLE #temptable (col1 int);  
GO  
INSERT INTO #temptable  
VALUES (10);  
GO  
SELECT * FROM #temptable;  
GO  
IF OBJECT_ID(N'tempdb..#temptable', N'U') IS NOT NULL   
DROP TABLE #temptable;  
GO  
--Test the drop.  
SELECT * FROM #temptable;  
  
```  
  
### <a name="d-dropping-a-table-using-if-exists"></a>D. 卸除資料表，使用 IF EXISTS  
  
**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。  
  
 下列範例會建立名為 T1 的資料表。 然後在第二個陳述式卸除資料表。 第三個陳述式會執行任何動作因為已刪除的資料表，但不會造成錯誤。  
  
```  
CREATE TABLE T1 (Col1 int);  
GO  
DROP TABLE IF EXISTS T1;  
GO  
DROP TABLE IF EXISTS T1;  
```  
  
  
## <a name="see-also"></a>另請參閱  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [TRUNCATE TABLE &#40;TRANSACT-SQL &#41;](../../t-sql/statements/truncate-table-transact-sql.md)   
 [卸除檢視 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-view-transact-sql.md)   
 [卸除程序 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-procedure-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  

