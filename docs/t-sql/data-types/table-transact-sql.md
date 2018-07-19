---
title: table (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table data type [SQL Server]
- table variables [SQL Server]
ms.assetid: 1ef0b60e-a64c-4e97-847b-67930e3973ef
caps.latest.revision: 48
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 035060bb8c9b0f31d6f8712d0abf94b2cf1c2939
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432237"
---
# <a name="table-transact-sql"></a>資料表 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

一種特殊的資料類型，可用於儲存結果集以供後續處理。 **table** 主要用來暫時儲存資料列集，此資料列集會當作資料表值函式的結果集傳回。 函式和變數可以宣告為 **table** 類型。 **table** 變數可以在函式、預存程序和批次中使用。 若要宣告 **table** 類型的變數，請使用 [DECLARE @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)。
  

**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 透過 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
table_type_definition ::=   
    TABLE ( { <column_definition> | <table_constraint> } [ ,...n ] )   
  
<column_definition> ::=   
    column_name scalar_data_type   
    [ COLLATE <collation_definition> ]   
    [ [ DEFAULT constant_expression ] | IDENTITY [ ( seed , increment ) ] ]   
    [ ROWGUIDCOL ]   
    [ column_constraint ] [ ...n ]   
  
 <column_constraint> ::=   
    { [ NULL | NOT NULL ]   
    | [ PRIMARY KEY | UNIQUE ]   
    | CHECK ( logical_expression )   
    }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,...n ] )  
     | CHECK ( logical_expression )   
     }   
```  
  
## <a name="arguments"></a>引數  
*table_type_definition*  
這是在 CREATE TABLE 中，用來定義資料表的相同資訊子集。 資料表宣告包括資料行定義、名稱、資料類型和條件約束。 允許使用的條件約束類型只有 PRIMARY KEY、UNIQUE KEY 和 NULL。  
如需語法的詳細資訊，請參閱 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)、[CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)，及 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)。
  
*collation_definition*  
為 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 地區設定和比較樣式、Windows 地區設定和二進位標記法，或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定序所組成之資料行的定序。 若未指定 *collation_definition*，資料行就會繼承目前資料庫的定序。 如果將資料行定義為 Common Language Runtime (CLR) 使用者定義型別，此資料行便會繼承使用者定義型別的定序。
  
## <a name="remarks"></a>Remarks  
批次的 FROM 子句中可以依名稱來參考 **table** 變數，如以下範例所示：
  
```sql
SELECT Employee_ID, Department_ID FROM @MyTableVar;  
```  
  
在 FROM 子句之外，您必須遵循下列範例所示，使用別名來參考 **table** 變數：
  
```sql
SELECT EmployeeID, DepartmentID   
FROM @MyTableVar m  
JOIN Employee on (m.EmployeeID =Employee.EmployeeID AND  
   m.DepartmentID = Employee.DepartmentID);  
```  
  
若為查詢計畫不變更的小規模查詢，而且以重新編譯考量為主時，**table** 變數可提供下列優點：
-   **table** 變數的行為類似於區域變數。 它有一個定義妥善的範圍。 這是其宣告所在的函數、預存程序或批次。  
     在 **table** 變數的範圍內，您可以依照一般資料表的方式來使用它。 在 SELECT、INSERT、UPDATE 和 DELETE 陳述式中，任何使用資料表或資料表運算式的位置都可以套用它。 不過在下列陳述式中，不能使用 **table**：  
  
```sql
SELECT select_list INTO table_variable;
```
  
在定義 **table** 變數的函式、預存程序或批次結尾，會自動清除該變數。
  
-   沒有影響效能的成本考量選擇時，預存程序所用之 **table** 變數所造成的預存程序重新編譯，比使用暫存資料表時還少。  
-   包含 **table** 變數的交易，只會在 **table** 變數更新期間持續存在。 因此，**table** 變數需要較少的鎖定和記錄資源。  
  
## <a name="limitations-and-restrictions"></a>限制事項
**Table** 變數沒有散發統計資料，並不會觸發重新編譯。 因此，在許多情況下，最佳化工具都將以資料表變數沒有資料列當做假設前提，建立查詢計劃。 基於這個原因，若您預期會有較多數目的資料列 (超過 100 列)，就應該謹慎使用資料表變數。 如果是這類情況，暫存資料表也許是更適宜的方案。 或者，如果查詢聯結資料表變數與其他資料表，則可使用 RECOMPILE 提示，以致使最佳化工具針對資料表變數使用正確的基數。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 最佳化工具的成本考量推論模型不支援 **table** 變數。 因此，需要成本考量選擇來達成有效率的查詢計劃時，就不應該使用這些變數。 需要成本考量選擇時，最好使用暫存資料表。 這種資料表通常會包含具有聯結的查詢、平行處理原則決定，以及索引選取範圍選擇。
  
修改 **table** 變數的查詢不會產生平行查詢執行計畫。 修改超大型 **table** 變數或複雜查詢中的 **table** 變數時，可能會影響效能。 在這些狀況中，請改用暫存資料表。 如需詳細資訊，請參閱 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)。 讀取但不修改 **table** 變數的查詢仍然可以平行處理。
  
您無法明確建立 **table** 變數的索引，也無法保留 **table** 變數的任何統計資料。 從 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 開始， 已引進新的語法，允許您建立某些內嵌資料表定義的索引類型。  您可以使用這個新的語法在 **table** 變數上建立索引，作為資料表定義的一部分。 在某些情況下，改用完整索引支援和統計資料的暫存資料表可以提升效能。 如需暫存資料表和建立內嵌索引的詳細資訊，請參閱 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)。


**table** 類型宣告中的 CHECK 條件約束、DEFAULT 值和計算資料行無法呼叫使用者定義函式。
  
不支援 **table** 變數之間的指派作業。
  
由於 **table** 變數的範圍受到限制，且不是持續性資料庫的一部分；因此，它們不會受交易回復的影響。
  
資料表變數在建立之後無法修改。
  
## <a name="examples"></a>範例  
  
### <a name="a-declaring-a-variable-of-type-table"></a>A. 宣告類型資料表的變數  
下列範例會建立一個 `table` 變數來儲存 UPDATE 陳述式的 OUTPUT 子句所指定的值。 之後的兩個 `SELECT` 陳述式會傳回 `@MyTableVar` 中的值，以及 `Employee` 資料表中更新作業的結果。 請注意，`INSERTED.ModifiedDate` 資料行中的結果不同於 `Employee` 資料表中 `ModifiedDate` 資料行的值。 這是因為將 `AFTER UPDATE` 值更新成目前日期的 `ModifiedDate` 觸發程序是定義在 `Employee` 資料表上。 不過，從 `OUTPUT` 傳回的資料行會反映引發觸發程序之前的資料。 如需詳細資訊，請參閱 [OUTPUT 子句 &#40;Transact-SQL&#41;](../../t-sql/queries/output-clause-transact-sql.md)。
  
```sql
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25   
OUTPUT INSERTED.BusinessEntityID,  
       DELETED.VacationHours,  
       INSERTED.VacationHours,  
       INSERTED.ModifiedDate  
INTO @MyTableVar;  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
--Note that ModifiedDate reflects the value generated by an  
--AFTER UPDATE trigger.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-creating-an-inline-table-valued-function"></a>B. 建立內嵌資料表值函式  
下列範例會傳回內嵌資料表值函式。 它會傳回三個資料行：`ProductID`、`Name`，以及年初至今銷售到商店之每項產品的總計彙總 `YTD Total` (依商店區分)。
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
GO  
```  
  
若要叫用函數，請執行這項查詢。
  
```sql
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
## <a name="see-also"></a>另請參閱
[COLLATE &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)  
[使用者定義的函式](../../relational-databases/user-defined-functions/user-defined-functions.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[使用資料表值參數 &#40;資料庫引擎&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)  
[查詢提示 &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)
  
  
