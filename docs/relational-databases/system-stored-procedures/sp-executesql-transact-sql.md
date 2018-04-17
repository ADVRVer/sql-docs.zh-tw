---
title: sp_executesql (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_executesql
- sp_executesql_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_executesql
- dynamic SQL
ms.assetid: a8d68d72-0f4d-4ecb-ae86-1235b962f646
caps.latest.revision: 64
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 29c2557584393605ba0e89f45dc079dea6d5ddb8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="spexecutesql-transact-sql"></a>sp_executesql (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  執行可重複使用許多次或已動態建立的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或批次。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或批次可包含內嵌參數。  
  
> [!IMPORTANT]  
>  執行階段編譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式可能會讓應用程式面臨惡意攻擊的威脅。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_executesql [ @stmt = ] statement  
[   
  { , [ @params = ] N'@parameter_name data_type [ OUT | OUTPUT ][ ,...n ]' }   
     { , [ @param1 = ] 'value1' [ ,...n ] }  
]  
```  
  
## <a name="arguments"></a>引數  
 [ @stmt=]*陳述式*  
 是 Unicode 字串，包含[!INCLUDE[tsql](../../includes/tsql-md.md)]陳述式或批次。 @stmt 必須是 Unicode 常數或 Unicode 變數。 不允許使用比較複雜的 Unicode 運算式，如用 + 運算子來串連兩個字串。 不允許使用字元常數。 如果指定了 Unicode 常數，它必須在前面加上**N**。例如，Unicode 常數**N'SP_WHO '**有效，但字元常數**'sp_who'**不是。 字串大小只受到可用資料庫伺服器記憶體的限制。 在 64 位元伺服器上限制為 2 GB，最大的大小字串的大小是**nvarchar （max)**。  
  
> [!NOTE]  
>  @stmt 可以包含參數具有相同的形式的變數名稱，例如： `N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 在 @stmt 參數定義清單和參數值清單中，@params 所包含的每個參數都必須有對應的項目。  
  
 [ @params=] N'@*parameter_name * * data_type* [，...*n* ] '  
 這是包含 @stmt 的所有內嵌參數定義的字串。此字串必須是 Unicode 常數或 Unicode 變數。 每個參數定義都由參數名稱和資料類型組成。 *n*是指出其他參數定義的預留位置。 指定在每個參數@stmtmust中定義@params。 如果 @stmt 中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或批次不包含參數，就不需要 @params。 這個參數的預設值是 NULL。  
  
 [ @param1= ] '*value1*'  
 這是參數字串所定義的第一個參數的值。 這個值可以是 Unicode 常數或 Unicode 變數。 @stmt 所包含的每個參數都必須有提供的參數值。當 @stmt 中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或批次沒有參數時，便不需要值。  
  
 [ OUT | OUTPUT ]  
 指出這個參數是輸出參數。 **文字**， **ntext**，和**映像**參數可用來當做輸出參數，除非此程序是 common language runtime (CLR) 程序。 除非此程序是一個 CLR 程序，否則使用 OUTPUT 關鍵字的輸出參數可以是資料指標預留位置。  
  
 *n*  
 這是其他參數值的預留位置。 這些值只能是常數或變數。 這些值不能是比較複雜的運算式，如函數或利用運算子來建立的運算式。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或非零 (失敗)  
  
## <a name="result-sets"></a>結果集  
 從內建在 SQL 字串內的所有 SQL 陳述式中傳回結果集。  
  
## <a name="remarks"></a>備註  
 必須以特定順序輸入 sp_executesql 參數，如稍早在本主題中 「 語法 」 一節中所述。 如果未按順序輸入參數，就會出現錯誤訊息。  
  
 關於批次、名稱範圍和資料庫內容，sp_executesql 的行為和 EXECUTE 相同。 [!INCLUDE[tsql](../../includes/tsql-md.md)]陳述式或批次中 sp_executesql @stmt sp_executesql 陳述式執行之前，不會編譯參數。 之後，就會編譯 @stmt 的內容，且會在稱為 sp_executesql 之批次的執行計畫之外，個別將它當做一項執行計畫來執行。 sp_executesql 批次無法參考稱為 sp_executesql 的批次中所宣告的變數。 稱為 sp_executesql 的批次看不到 sp_executesql 批次中的本機資料指標或變數。 資料庫內容中的變更會持續到 sp_executesql 陳述式結束。  
  
 當陳述式參數值的變更是唯一的變數時，您可以利用 sp_executesql 取代預存程序來重複執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。 由於 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式本身維持不變，只有參數值改變，因此，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查詢最佳化工具可能會重複使用它針對第一次執行所產生的執行計畫。  
  
> [!NOTE]  
>  若要提升效能，請在陳述式字串中使用完整物件名稱。  
  
 如下列範例所示，sp_executesql 支援在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 字串之外個別設定參數值。  
  
```  
DECLARE @IntVariable int;  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
  
/* Build the SQL string one time.*/  
SET @SQLString =  
     N'SELECT BusinessEntityID, NationalIDNumber, JobTitle, LoginID  
       FROM AdventureWorks2012.HumanResources.Employee   
       WHERE BusinessEntityID = @BusinessEntityID';  
SET @ParmDefinition = N'@BusinessEntityID tinyint';  
/* Execute the string with the first parameter value. */  
SET @IntVariable = 197;  
EXECUTE sp_executesql @SQLString, @ParmDefinition,  
                      @BusinessEntityID = @IntVariable;  
/* Execute the same string with the second parameter value. */  
SET @IntVariable = 109;  
EXECUTE sp_executesql @SQLString, @ParmDefinition,  
                      @BusinessEntityID = @IntVariable;  
```  
  
 輸出參數也可以搭配 sp_executesql 使用。 下列範例會從 `AdventureWorks2012.HumanResources.Employee` 資料表中擷取一個職稱，並在輸出參數 `@max_title` 中將它傳回。  
  
```  
DECLARE @IntVariable int;  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
DECLARE @max_title varchar(30);  
  
SET @IntVariable = 197;  
SET @SQLString = N'SELECT @max_titleOUT = max(JobTitle)   
   FROM AdventureWorks2012.HumanResources.Employee  
   WHERE BusinessEntityID = @level';  
SET @ParmDefinition = N'@level tinyint, @max_titleOUT varchar(30) OUTPUT';  
  
EXECUTE sp_executesql @SQLString, @ParmDefinition, @level = @IntVariable, @max_titleOUT=@max_title OUTPUT;  
SELECT @max_title;  
```  
  
 在 sp_executesql 中替換參數的能力，會為利用 EXECUTE 陳述式來執行字串帶來下列好處：  
  
-   由於在各次執行之間，sp_executesql 字串中 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的實際文字不會改變，因此，查詢最佳化工具可能會符合第二次執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式與針對第一次執行所產生的執行計畫。 因此，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不需要編譯第二個陳述式。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] 字串只建立一次。  
  
-   整數參數用原生格式來指定。 不需要轉換成 Unicode。  
  
## <a name="permissions"></a>Permissions  
 需要 public 角色中的成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-executing-a-simple-select-statement"></a>A. 執行簡單的 SELECT 陳述式  
 下列範例會建立和執行包含名稱為 `SELECT` 的內嵌參數之簡單 `@level` 陳述式。  
  
```  
EXECUTE sp_executesql   
          N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
          WHERE BusinessEntityID = @level',  
          N'@level tinyint',  
          @level = 109;  
```  
  
### <a name="b-executing-a-dynamically-built-string"></a>B. 執行動態建立的字串  
 下列範例會示範如何利用 `sp_executesql` 來執行動態建立的字串。 這個範例預存程序會將資料插入一組用來分割年度銷售資料的資料表中。 年度每個月份都有一份資料表，格式如下：  
  
```  
CREATE TABLE May1998Sales  
    (OrderID int PRIMARY KEY,  
    CustomerID int NOT NULL,  
    OrderDate  datetime NULL  
        CHECK (DATEPART(yy, OrderDate) = 1998),  
    OrderMonth int  
        CHECK (OrderMonth = 5),  
    DeliveryDate datetime  NULL,  
        CHECK (DATEPART(mm, OrderDate) = OrderMonth)  
    )  
```  
  
 這個範例預存程序會動態建立和執行 `INSERT` 陳述式，以便將新的訂單插入正確的資料表中。 這個範例利用訂購日期來建立應該包含資料之資料表的名稱，再將這個名稱納入 `INSERT` 陳述式中。  
  
> [!NOTE]  
>  這是 sp_executesql 的簡單範例。 這個範例不包含錯誤檢查，也不包括商務規則的檢查，如保證訂單號碼在資料表之間不重複。  
  
```  
CREATE PROCEDURE InsertSales @PrmOrderID INT, @PrmCustomerID INT,  
                 @PrmOrderDate DATETIME, @PrmDeliveryDate DATETIME  
AS  
DECLARE @InsertString NVARCHAR(500)  
DECLARE @OrderMonth INT  
  
-- Build the INSERT statement.  
SET @InsertString = 'INSERT INTO ' +  
       /* Build the name of the table. */  
       SUBSTRING( DATENAME(mm, @PrmOrderDate), 1, 3) +  
       CAST(DATEPART(yy, @PrmOrderDate) AS CHAR(4) ) +  
       'Sales' +  
       /* Build a VALUES clause. */  
       ' VALUES (@InsOrderID, @InsCustID, @InsOrdDate,' +  
       ' @InsOrdMonth, @InsDelDate)'  
  
/* Set the value to use for the order month because  
   functions are not allowed in the sp_executesql parameter  
   list. */  
SET @OrderMonth = DATEPART(mm, @PrmOrderDate)  
  
EXEC sp_executesql @InsertString,  
     N'@InsOrderID INT, @InsCustID INT, @InsOrdDate DATETIME,  
       @InsOrdMonth INT, @InsDelDate DATETIME',  
     @PrmOrderID, @PrmCustomerID, @PrmOrderDate,  
     @OrderMonth, @PrmDeliveryDate  
  
GO  
```  
  
 在這個程序中使用 sp_executesql，比利用 EXECUTE 來執行字串有效。 當使用 sp_executesql 時，只會產生 12 個 INSERT 字串版本，每月資料表各一個。 當使用 EXECUTE 時，每個 INSERT 字串都是唯一的，因為參數值不同。 雖然這兩個方法會產生相同的批次數目，但 sp_executesql 所產生之 INSERT 字串的類似性，使得查詢最佳化工具更可能重複使用執行計畫。  
  
### <a name="c-using-the-output-parameter"></a>C. 使用 OUTPUT 參數  
 下列範例會使用`OUTPUT`參數來儲存所產生的結果集`SELECT`陳述式中的`@SQLString`參數。兩個`SELECT`陳述式接著會執行所使用的值`OUTPUT`參數。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
DECLARE @SalesOrderNumber nvarchar(25);  
DECLARE @IntVariable int;  
SET @SQLString = N'SELECT @SalesOrderOUT = MAX(SalesOrderNumber)  
    FROM Sales.SalesOrderHeader  
    WHERE CustomerID = @CustomerID';  
SET @ParmDefinition = N'@CustomerID int,  
    @SalesOrderOUT nvarchar(25) OUTPUT';  
SET @IntVariable = 22276;  
EXECUTE sp_executesql  
    @SQLString  
    ,@ParmDefinition  
    ,@CustomerID = @IntVariable  
    ,@SalesOrderOUT = @SalesOrderNumber OUTPUT;  
-- This SELECT statement returns the value of the OUTPUT parameter.  
SELECT @SalesOrderNumber;  
-- This SELECT statement uses the value of the OUTPUT parameter in  
-- the WHERE clause.  
SELECT OrderDate, TotalDue  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderNumber = @SalesOrderNumber;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-executing-a-simple-select-statement"></a>D. 執行簡單的 SELECT 陳述式  
 下列範例會建立和執行包含名稱為 `SELECT` 的內嵌參數之簡單 `@level` 陳述式。  
  
```  
-- Uses AdventureWorks  
  
EXECUTE sp_executesql   
          N'SELECT * FROM AdventureWorksPDW2012.dbo.DimEmployee   
          WHERE EmployeeKey = @level',  
          N'@level tinyint',  
          @level = 109;  
```  
  
 如需其他範例，請參閱[sp_executesql (TRANSACT-SQL)](http://msdn.microsoft.com/library/ms188001.aspx)。  
  
## <a name="see-also"></a>另請參閱  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
