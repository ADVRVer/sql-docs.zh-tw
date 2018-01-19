---
title: "SELECT 子句 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT Clause
- SELECT_Clause_TSQL
- DISTINCT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- parentheses [SQL Server]
- identity columns [SQL Server], SELECT clause
- SELECT clause
- $IDENTITY keyword
- user-defined types [SQL Server], invoking methods and properties
- SELECT statement [SQL Server], processing orders
- clauses [SQL Server], SELECT
- $ROWGUID keyword
- queries [SQL Server], results
ms.assetid: 2616d800-4853-4cf1-af77-d32d68d8c2ef
caps.latest.revision: "54"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8aa26314b450d859760f69b61887827b73b456fc
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="select-clause-transact-sql"></a>SELECT 子句 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定查詢所要傳回的資料行。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
SELECT [ ALL | DISTINCT ]  
[ TOP ( expression ) [ PERCENT ] [ WITH TIES ] ]   
<select_list>   
<select_list> ::=   
    {   
      *   
      | { table_name | view_name | table_alias }.*   
      | {  
          [ { table_name | view_name | table_alias }. ]  
               { column_name | $IDENTITY | $ROWGUID }   
          | udt_column_name [ { . | :: } { { property_name | field_name }   
            | method_name ( argument [ ,...n] ) } ]  
          | expression  
          [ [ AS ] column_alias ]   
         }  
      | column_alias = expression   
    } [ ,...n ]   
```  
  
## <a name="arguments"></a>引數  
 **ALL**  
 指定結果集中可以有重複的資料列。 ALL 是預設值。  
  
 DISTINCT  
 指定結果集中只能有不重複的資料列 (唯一資料列)。 針對 DISTINCT 關鍵字的用途，Null 值會被視為相等。  
  
 TOP (*expression* ) [ PERCENT ] [ WITH TIES ]  
 指出只有指定的第一組資料列或資料列百分比會從查詢結果集傳回。 *expression* 可以是一個數字，也可以是資料列的百分比。  
  
 回溯相容性，使用 TOP*運算式*沒有括號在 SELECT 陳述式支援，但我們不建議您這麼做。 如需詳細資訊，請參閱[TOP &#40;TRANSACT-SQL &#41;](../../t-sql/queries/top-transact-sql.md).  
  
\<select_list > 要選取的結果集的資料行。 選取清單是一系列運算式 (以逗號分隔)。 選取清單中所能指定的最大運算式數目是 4096。  
  
 \*  
 指定應該傳回 FROM 子句中所有資料表和檢視的所有資料行。 依照 FROM 子句所指定，資料表或檢視會傳回這些資料行，且會遵照它們在資料表或檢視中的順序。  
  
 *table_name* | *view_name* | *資料表*_*別名*。 *  
 範圍限制\*至指定的資料表或檢視表。  
  
 *column_name*  
 這是要傳回的資料行名稱。 限定*column_name*若要避免模稜兩可的參考，例如發生於兩個資料表的 FROM 子句中有重複的名稱資料行。 例如，SalesOrderHeader 和 SalesOrderDetail 資料表中的[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]這兩個資料庫有一個名稱為 ModifiedDate 的資料行。 如果在查詢中聯結兩份資料表，您可以在選取清單中，將 SalesOrderDetail 項目的修改日期指定為 SalesOrderDetail.ModifiedDate。  
  
 *expression*  
 這是一個常數、函數，或由一個或多個運算子連接之資料行名稱、常數和函數的任意組合，或子查詢。  
  
 $IDENTITY  
 傳回識別欄位。 如需詳細資訊，請參閱[身分識別 &#40;屬性 &#41;&#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)， [ALTER 資料表 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-table-transact-sql.md)，和[建立資料表 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
 如果 FROM 子句中有多份資料表有含 IDENTITY 屬性的資料行，就必須利用特定資料表名稱來限定 $IDENTITY，例如 T1.$IDENTITY。  
  
 $ROWGUID   
 傳回資料列 GUID 資料行。  
  
 如果 FROM 子句中有多份資料表含有 ROWGUIDCOL 屬性，就必須利用特定資料表名稱來限定 $ROWGUID，例如 T1.$ROWGUID。  
  
 *udt_column_name*  
 這是要傳回的 Common Language Runtime (CLR) 使用者自訂類型資料行名稱。  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 會傳回二進位表示法的使用者自訂類型值。 若要在字串或 XML 格式傳回使用者定義型別值，請使用[轉換](../../t-sql/functions/cast-and-convert-transact-sql.md)或[轉換](../../t-sql/functions/cast-and-convert-transact-sql.md)。  
  
 { . | :: }  
 指定 CLR 使用者自訂類型的方法、屬性或欄位。 使用。 。 如果是靜態方法、屬性或欄位，請使用 ::。 若要叫用 CLR 使用者自訂類型的方法、屬性或欄位，您必須具有類型的 EXECUTE 權限。  
  
 *property_name*  
 是的公用屬性*udt_column_name*。  
  
 *field_name*  
 公用資料成員的*udt_column_name*。  
  
 *method_name*  
 公用方法*udt_column_name*接受一或多個引數。 *method_name*不能是 mutator 方法。  
  
 下列範例會叫用稱為 `Location` 之類型的方法，從 `point` 資料表中選取定義為 `Cities` 類型的 `Distance` 資料行值：  
  
```  
CREATE TABLE dbo.Cities (  
     Name varchar(20),  
     State varchar(20),  
     Location point );  
GO  
DECLARE @p point (32, 23), @distance float;  
GO  
SELECT Location.Distance (@p)  
FROM Cities;  
```  
  
 *column_ 別名*  
 這是取代查詢結果集中之資料行名稱的替代名稱。 例如，名稱為 Quantity 的資料行，可以指定 Quantity 或 Quantity to Date 或 Qty 之類的別名。  
  
 另外，別名也用來指定運算式結果的名稱，例如：  
  
 ```sql
 USE AdventureWorks2012;  
 GO  
 SELECT AVG(UnitPrice) AS [Average Price]  
 FROM Sales.SalesOrderDetail;
 ```  
  
 *column_alias*可用在 ORDER BY 子句中。 不過，它不能用在 WHERE、GROUP BY 或 HAVING 子句中。 如果查詢運算式是 DECLARE CURSOR 陳述式的一部分*column_alias*不能在 FOR UPDATE 子句。  
  
## <a name="remarks"></a>備註  
 傳回的資料長度**文字**或**ntext**包含選取清單中的資料行設定為下列的最小值： 的實際大小**文字**資料行、 預設 TEXTSIZE 工作階段設定或硬式編碼的應用程式限制。 若要變更工作階段傳回文字的長度，請使用 SET 陳述式。 依預設，SELECT 陳述式傳回的文字資料長度限制是 4,000 個位元組。  
  
 如果發生下列中的任何行為，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會引發 511 例外狀況，且會回復目前在執行中的陳述式：  
  
-   SELECT 陳述式產生超出 8,060 位元組的結果資料列或中繼工作資料表資料列。  
  
-   DELETE、INSERT 或 UPDATE 陳述式試圖處理超出 8,060 位元組的資料列。  
  
 如果 SELECT INTO 或 CREATE VIEW 陳述式所建立的資料行未指定資料行名稱，便會發生錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [精選的範例 &#40;TRANSACT-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)   
 [運算式 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  
