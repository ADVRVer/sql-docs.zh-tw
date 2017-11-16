---
title: "使用 AUTO 模式自動格式化 JSON 輸出 (SQL Server) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FOR JSON AUTO
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ccb93d0bb891f13fc0af0bc1c3ff4e8e6d1293cd
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>使用 AUTO 模式自動格式化 JSON 輸出 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

若要根據 **SELECT** 陳述式之結構自動格式化 **FOR JSON** 子句的輸出，請指定 **AUTO** 選項。  
  
當您指定 **AUTO** 選項時，會根據 SELECT 清單中的資料行順序和其來源資料表自動決定 JSON 輸出格式。 您無法變更此格式。
 
替代方法是使用 **PATH** 選項來維護輸出的控制權。
-   如需 **PATH** 選項的詳細資訊，請參閱[以 PATH 模式格式化巢狀的 JSON 輸出](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md)。
-   如需這兩個選項的概觀，請參閱[使用 FOR JSON 將查詢結果格式化為 JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)。

使用 **FOR JSON AUTO** 選項的查詢必須具有 **FROM** 子句。  
  
以下是 **FOR JSON** 子句搭配 **AUTO** 選項的一些範例。  
  
## <a name="examples"></a>範例

### <a name="example-1"></a>範例 1
 **查詢**  
  
如果查詢只參考一個資料表，FOR JSON AUTO 子句的結果會類似於 FOR JSON PATH 的結果。 在此情況下，FOR JSON AUTO 不會建立巢狀物件。 唯一的差別在於 FOR JSON AUTO 會輸出以點分隔的別名 (例如，下列範例中的 `Info.MiddleName`) 作為含點的索引鍵，而不是巢狀物件。  
  
```sql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON AUTO  
```  
  
 **結果**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sánchez",
    "Info.MiddleName": "J"
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info.MiddleName": "Lee"
}, {
    "Id": 3,
    "FirstName": "Roberto",
    "LastName": "Tamburello"
}, {
    "Id": 4,
    "FirstName": "Rob",
    "LastName": "Walters"
}, {
    "Id": 5,
    "FirstName": "Gail",
    "LastName": "Erickson",
    "Info.Title": "Ms.",
    "Info.MiddleName": "A"
}]
```  

### <a name="example-2"></a>範例 2

**查詢**  
  
聯結資料表時，第一個資料表中的資料行會產生為根物件的屬性。 第二個資料表中的資料行則會產生為巢狀物件的屬性。 第二個資料表的資料表名稱或別名 (例如，下列範例中的 `D`) 可作為巢狀陣列的名稱。  
  
```sql  
SELECT TOP 2 SalesOrderNumber,  
        OrderDate,  
        UnitPrice,  
        OrderQty  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON AUTO   
```  
  
**結果**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO43659",
    "D": [{
        "UnitPrice": 34.40
    }, {
        "UnitPrice": 134.24,
        "OrderQty": 5
    }]
}]
```  

### <a name="example-3"></a>範例 3
 
**查詢**  
您可以將 FOR JSON PATH 子查詢巢狀於 SELECT 陳述式，而不是使用 FOR JSON AUTO，如下列範例所示。 此範例所輸出的結果與上述範例相同。  
  
```sql  
SELECT TOP 2  
    SalesOrderNumber,  
    OrderDate,  
    (SELECT UnitPrice, OrderQty  
      FROM Sales.SalesOrderDetail AS D  
      WHERE H.SalesOrderID = D.SalesOrderID  
     FOR JSON PATH) AS D  
FROM Sales.SalesOrderHeader AS H  
FOR JSON PATH  
```  
  
**結果**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO4390",
    "D": [{
        "UnitPrice": 24.99
    }]
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>深入了解 SQL Server 中的內建 JSON 支援  
對於大量的特定解決方案、使用案例和建議，請參閱 SQL Server 和 Azure SQL Database 中 Microsoft 經理專案 Jovan Popovic 所撰寫的[有關內建 JSON 支援的部落格文章](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)。

## <a name="see-also"></a>另請參閱  
 [FOR 子句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
