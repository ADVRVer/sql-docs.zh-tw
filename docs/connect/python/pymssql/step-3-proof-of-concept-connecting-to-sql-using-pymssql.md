---
title: 步驟 3：使用 pymssql 連線至 SQL
description: 步驟 3 是一個概念證明，說明如何使用 Python 和 pymssql 連線至 SQL Server。 基本範例示範如何選取和插入資料。
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2246ddeb-7c2f-46f3-8a91-cdd718d39b40
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1c75d13e9e44632c411639385227776f54ca1a9
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528562"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>步驟 3：使用 pymssql 連線到 SQL 的概念證明
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

這個範例只應被視為一個概念證明。  為了清楚起見，已將範例程式碼簡化，而其不一定代表 Microsoft 建議的最佳做法。  
  
## <a name="step-1--connect"></a>步驟 1:連線  
  
[pymssql.connect](https://pypi.org/project/pymssql/) 函式可用來連接到 SQL Database。  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>步驟 2:執行查詢  
  
[cursor.execute](https://pypi.org/project/pymssql/) 函式可用來擷取對 SQL Database 查詢的結果集。 這個函式基本上會接受任何查詢並傳回結果集，您可以使用 [cursor.fetchone()](https://pypi.org/project/pymssql/) 反覆查詢結果集。  
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute('SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC;')  
    row = cursor.fetchone()  
    while row:  
        print str(row[0]) + " " + str(row[1]) + " " + str(row[2])     
        row = cursor.fetchone()  
```  
  
## <a name="step-3--insert-a-row"></a>步驟 3：插入資料列  
  
在此範例中，您將了解如何安全地執行 [INSERT](../../../t-sql/statements/insert-transact-sql.md) 陳述式，並傳遞參數。 將參數作為值傳遞，可協助您的應用程式防禦 [SQL 插入](../../../relational-databases/tables/primary-and-foreign-key-constraints.md)。  
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express', 'SQLEXPRESS', 0, 0, CURRENT_TIMESTAMP)")  
    row = cursor.fetchone()  
    while row:  
        print "Inserted Product ID : " +str(row[0])  
        row = cursor.fetchone()  
    conn.commit()
    conn.close()
```  
  
## <a name="step-4-roll-back-a-transaction"></a>步驟 4：復原交易  
  
這個程式碼範例示範如何使用交易，您將：  
  
* 開始交易  
* 插入一列資料  
* 復原您的交易以復原插入  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("BEGIN TRANSACTION")  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, CURRENT_TIMESTAMP)")  
    conn.rollback()  
    conn.close()
```  
    
  ## <a name="next-steps"></a>後續步驟  
  
如需詳細資訊，請參閱 [Python 開發人員中心](https://azure.microsoft.com/develop/python/)。
