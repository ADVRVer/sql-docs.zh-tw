---
title: "DBCC CLEANTABLE (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLEANTABLE_TSQL
- DBCC_CLEANTABLE_TSQL
- DBCC CLEANTABLE
- CLEANTABLE
dev_langs:
- TSQL
helpviewer_keywords:
- disk space [SQL Server], reclaiming
- reclaiming space
- reallocating space
- removing columns
- DBCC CLEANTABLE statement
- space [SQL Server], reclaiming
- deleting columns
- dropping columns
ms.assetid: 0dbbc956-15b1-427b-812c-618a044d07fa
caps.latest.revision: 53
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7152b7241d97953fdeddf343dbeea60ed8d7ff5f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-cleantable-transact-sql"></a>DBCC CLEANTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]回收空間，以從資料表或索引檢視表中已卸除的可變長度資料行。
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
  
DBCC CLEANTABLE  
(  
    { database_name | database_id | 0 }  
    , { table_name | table_id | view_name | view_id }  
    [ , batch_size ]  
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引數  
 *database_name* | *database_id* | 0  
 這是要清除之資料表所屬的資料庫。 如果指定 0，就會使用目前的資料庫。 資料庫名稱必須遵循的規則[識別碼](../../relational-databases/databases/database-identifiers.md)。  
  
 *table_name* | *table_id* | *view_name*| *view_id*  
 這是要清除的資料表或索引檢視。  
  
 *batch_size*  
 這是每項交易所處理的資料列數。 若未指定，或指定 0，陳述式就會在單一交易中處理整份資料表。  
  
 WITH NO_INFOMSGS  
 隱藏所有參考訊息。  
  
## <a name="remarks"></a>備註  
DBCC CLEANTABLE 會在可變長度資料行卸除之後回收空間。 可變長度資料行可以是下列一種資料類型： **varchar**， **nvarchar**， **varchar （max)**， **nvarchar （max)**， **varbinary**， **varbinary （max)**，**文字**， **ntext**，**映像**， **sql_variant**，和**xml**。 在卸除固定長度資料行之後，這個命令並不會回收空間。
如果卸除的資料行之前是儲存在同資料列，則 DBCC CLEANTABLE 會從資料表的 IN_ROW_DATA 配置單位回收空間。 如果資料行儲存在非資料列中，則會根據卸除資料行的資料類型，從 ROW_OVERFLOW_DATA 或 LOB_DATA 配置單位回收空間。 如果從 ROW_OVERFLOW_DATA 或 LOB_DATA 頁面回收空間會導致空頁面，則 DBCC CLEANTABLE 會將頁面移除。
DBCC CLEANTABLE 可以執行為一或多項交易。 如果未指定批次大小，這個命令會在單一交易中處理整份資料表，在作業期間，會獨佔鎖定這份資料表。 對於某些大型資料表而言，單一交易的長度及所需要的記錄空間可能會太大。 如果指定了批次大小，便會在一系列交易中執行這個命令，每項交易都包含指定數目的資料列。 DBCC CLEANTABLE 無法作為另一項交易內的交易來執行。
這項作業會完整記錄下來。
不支援在系統資料表、暫存資料表或資料表之 xVelocity 記憶體最佳化的資料行存放區索引部分中使用 DBCC CLEANTABLE。
  
## <a name="best-practices"></a>最佳作法  
DBCC CLEANTABLE 不應當做例行維護工作來執行， 而應該在對資料表或索引檢視中的可變長度資料行進行了大幅變更，而且需要立即回收未使用空間時，使用 DBCC CLEANTABLE。 或者，您可以在資料表或檢視上重建索引；不過，這項作業可能會需要大量的資源。
  
## <a name="result-sets"></a>結果集  
DBCC CLEANTABLE 會傳回：
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
 呼叫端必須擁有資料表或索引檢視表，或是屬於**sysadmin**固定伺服器角色、 **db_owner**固定資料庫角色或**db_ddladmin**固定的資料庫角色。  
  
## <a name="examples"></a>範例  
### <a name="a-using-dbcc-cleantable-to-reclaim-space"></a>A. 使用 DBCC CLEANTABLE 來回收空間  
下列範例會針對 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫中的 `Production.Document` 資料表執行 DBCC CLEANTABLE。
  
```sql  
DBCC CLEANTABLE (AdventureWorks2012,'Production.Document', 0)  
WITH NO_INFOMSGS;  
GO  
```  
  
### <a name="b-using-dbcc-cleantable-and-verifying-results"></a>B. 使用 DBCC CLEANTABLE 並確認結果  
下列範例會建立並擴展具有數個可變長度資料行的資料表。 接著將卸除兩個資料行，然後執行 DBCC CLEANTABLE 以回收未使用的空間。 還會在執行 DBCC CLEANTABLE 命令前後執行查詢，以確認頁數和使用空間值。
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('dbo.CleanTableTest', 'U') IS NOT NULL  
    DROP TABLE dbo.CleanTableTest;  
GO  
CREATE TABLE dbo.CleanTableTest  
    (FileName nvarchar(4000),   
    DocumentSummary nvarchar(max),  
    Document varbinary(max)  
    );  
GO  
-- Populate the table with data from the Production.Document table.  
INSERT INTO dbo.CleanTableTest  
    SELECT REPLICATE(FileName, 1000),   
           DocumentSummary,   
           Document  
    FROM Production.Document;  
GO  
-- Verify the current page counts and average space used in the dbo.CleanTableTest table.  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.dbo.CleanTableTest');  
SELECT alloc_unit_type_desc,   
       page_count,   
       avg_page_space_used_in_percent,   
       record_count  
FROM sys.dm_db_index_physical_stats(@db_id, @object_id, NULL, NULL , 'Detailed');  
GO  
-- Drop two variable-length columns from the table.  
ALTER TABLE dbo.CleanTableTest  
DROP COLUMN FileName, Document;  
GO  
-- Verify the page counts and average space used in the dbo.CleanTableTest table  
-- Notice that the values have not changed.  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.dbo.CleanTableTest');  
SELECT alloc_unit_type_desc,   
       page_count,   
       avg_page_space_used_in_percent,   
       record_count  
FROM sys.dm_db_index_physical_stats(@db_id, @object_id, NULL, NULL , 'Detailed');  
GO  
-- Run DBCC CLEANTABLE.  
DBCC CLEANTABLE (AdventureWorks2012,'dbo.CleanTableTest');  
GO  
-- Verify the values in the dbo.CleanTableTest table after the DBCC CLEANTABLE command.  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.dbo.CleanTableTest');  
SELECT alloc_unit_type_desc,   
       page_count,   
       avg_page_space_used_in_percent,   
       record_count  
FROM sys.dm_db_index_physical_stats(@db_id, @object_id, NULL, NULL , 'Detailed');  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
 [sys.allocation_units &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)  
  
  

