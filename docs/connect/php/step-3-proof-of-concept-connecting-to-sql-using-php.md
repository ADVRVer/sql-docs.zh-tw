---
title: 步驟 3︰使用 PHP 連線到 SQL 的概念證明
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a7451a85-18e5-4fd0-bbcb-2f15a1117290
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d685c15b4cc30dc093a47b37e6bfc29368e91f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68014797"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-php"></a>步驟 3︰使用 PHP 連接到 SQL 的概念證明
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="step-1--connect"></a>步驟 1: 連接  
  
  
這個**OpenConnection**函式會在接下來的所有函式中的頂端附近呼叫。  
  
  
```php 
    function OpenConnection()  
    {  
        try  
        {  
            $serverName = "tcp:myserver.database.windows.net,1433";  
            $connectionOptions = array("Database"=>"AdventureWorks",  
                "Uid"=>"MyUser", "PWD"=>"MyPassword");  
            $conn = sqlsrv_connect($serverName, $connectionOptions);  
            if($conn == false)  
                die(FormatErrors(sqlsrv_errors()));  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-2--execute-query"></a>步驟 2: 執行查詢  
  
[Sqlsrv_query ()](https://php.net/manual/en/function.sqlsrv-query.php)函數可用來從查詢針對 SQL Database 取出結果集。 此函式基本上會接受任何查詢和連線物件, 並傳回可使用[sqlsrv_fetch_array ()](https://php.net/manual/en/function.sqlsrv-fetch-array.php)反復執行的結果集。  
  
```php  
    function ReadData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
            $tsql = "SELECT [CompanyName] FROM SalesLT.Customer";  
            $getProducts = sqlsrv_query($conn, $tsql);  
            if ($getProducts == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
            $productCount = 0;  
            while($row = sqlsrv_fetch_array($getProducts, SQLSRV_FETCH_ASSOC))  
            {  
                echo($row['CompanyName']);  
                echo("<br/>");  
                $productCount++;  
            }  
            sqlsrv_free_stmt($getProducts);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
  
## <a name="step-3--insert-a-row"></a>步驟 3: 插入資料列  
  
在此範例中, 您將瞭解如何安全地執行[INSERT](../../t-sql/statements/insert-transact-sql.md)語句、傳遞可保護您的應用程式免于[SQL 插入](../../relational-databases/tables/primary-and-foreign-key-constraints.md)值的參數。    
  
  
```php 
    function InsertData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            $tsql = "INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT            INSERTED.ProductID VALUES ('SQL Server 1', 'SQL Server 2', 0, 0, getdate())";  
            //Insert query  
            $insertReview = sqlsrv_query($conn, $tsql);  
            if($insertReview == FALSE)  
                die(FormatErrors( sqlsrv_errors()));  
            echo "Product Key inserted is :";  
            while($row = sqlsrv_fetch_array($insertReview, SQLSRV_FETCH_ASSOC))  
            {     
                echo($row['ProductID']);  
            }  
            sqlsrv_free_stmt($insertReview);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-4--rollback-a-transaction"></a>步驟 4: 復原交易  
  
  
這個程式碼範例會示範交易的使用方式, 您可以在其中:  
  
-開始交易  
  
-插入一列資料, 更新另一個資料列  
  
-如果插入和更新成功, 則認可您的交易, 如果其中一個不是, 則回復交易  
  
  
```php 
    function Transactions()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            if (sqlsrv_begin_transaction($conn) == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
  
            $tsql1 = "INSERT INTO SalesLT.SalesOrderDetail (SalesOrderID,OrderQty,ProductID,UnitPrice)  
            VALUES (71774, 22, 709, 33)";  
            $stmt1 = sqlsrv_query($conn, $tsql1);  
  
            /* Set up and execute the second query. */  
            $tsql2 = "UPDATE SalesLT.SalesOrderDetail SET OrderQty = (OrderQty + 1) WHERE ProductID = 709";  
            $stmt2 = sqlsrv_query( $conn, $tsql2);  
  
            /* If both queries were successful, commit the transaction. */  
            /* Otherwise, rollback the transaction. */  
            if($stmt1 && $stmt2)  
            {  
                   sqlsrv_commit($conn);  
                   echo("Transaction was commited");  
            }  
            else  
            {  
                sqlsrv_rollback($conn);  
                echo "Transaction was rolled back.\n";  
            }  
            /* Free statement and connection resources. */  
            sqlsrv_free_stmt( $stmt1);  
            sqlsrv_free_stmt( $stmt2);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="additional-examples"></a>其他範例  
  
[範例應用程式 (SQLSRV 驅動程式)](../../connect/php/example-application-sqlsrv-driver.md)  

[範例應用程式 (PDO_SQLSRV 驅動程式)](../../connect/php/example-application-pdo-sqlsrv-driver.md)
