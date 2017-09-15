---
title: "步驟 3： 連接到使用 pymssql SQL 的概念證明 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2246ddeb-7c2f-46f3-8a91-cdd718d39b40
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 732e6fd574d80d58aef81a149acc54376231e6cc
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>步驟 3： 連接到使用 pymssql SQL 的概念證明
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

此範例中，應該考量只概念證明。  範例程式碼為了清楚起見，已簡化，並不一定代表由 Microsoft 所建議的最佳作法。  
  
## <a name="step-1--connect"></a>步驟 1： 連接  
  
[Pymssql.connect](http://pymssql.org/en/latest/ref/pymssql.html)函數用來連接到 SQL Database。  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>步驟 2： 執行查詢  
  
[Cursor.execute](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute)函式可以用來擷取結果集從查詢中，針對 SQL 資料庫。 此函式基本上會接受任何查詢，並傳回結果集的使用可逐一[cursor.fetchone()](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone)。  
  
  
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
  
## <a name="step-3--insert-a-row"></a>步驟 3： 插入資料列  
  
在您將了解如何執行此範例[插入](https://msdn.microsoft.com/library/ms174335.aspx)陳述式，將參數可保護您的應用程式，從[SQL 資料隱碼](https://technet.microsoft.com/library/ms161953(v=sql.105).aspx)弱點和擷取自動產生的[主索引鍵](https://msdn.microsoft.com/library/ms179610.aspx)值。    
  
  
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
  
## <a name="step-4--rollback-a-transaction"></a>步驟 4： 回復交易  
  
這個程式碼範例示範如何使用交易，在其中您：  
  
* 開始交易  
* 插入資料列  
* 復原您復原插入的交易  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("BEGIN TRANSACTION")  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, CURRENT_TIMESTAMP)")  
    conn.rollback()  
    conn.close()
```  
    
  ## <a name="next-steps"></a>後續的步驟  
  
如需詳細資訊，請參閱[Python 開發人員中心](https://azure.microsoft.com/en-us/develop/python/)。
