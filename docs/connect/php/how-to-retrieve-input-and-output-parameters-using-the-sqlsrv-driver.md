---
title: 如何： 擷取使用 SQLSRV 驅動程式的 I/O 參數 |Microsoft Docs
ms.custom: ''
ms.date: 04/12/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedure support
ms.assetid: 9a7c5f60-67f9-4968-a3a8-c256ee481da2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c865207156703d87ae827a3274e788b7b8bda270
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629926"
---
# <a name="how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver"></a>如何：使用 SQLSRV 驅動程式擷取輸入和輸出參數
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

本主題示範如何使用 SQLSRV 驅動程式呼叫將其中一個參數定義為輸入/輸出參數的預存程序，以及如何擷取結果。 在擷取輸出或輸入/輸出參數時，必須先取用預存程序所傳回的所有結果，傳回的參數值才可供存取。  
  
> [!NOTE]  
> 初始化或更新為 **null**、 **DateTime**或資料流類型的變數，無法作為輸出參數。  
  
## <a name="example-1"></a>範例 1
下列範例會呼叫從指定員工的可用休假時數中扣除掉已用休假時數的預存程序。 代表已用休假時數的變數 *$vacationHrs*，會傳遞至預存程序做為輸入參數。 在更新可用休假時數之後，預存程序會使用相同的參數傳回剩餘休假時數。  
  
> [!NOTE]  
> 將 *$vacationHrs* 初始化為 4，會將傳回的 PHPTYPE 設為整數。 若要確保資料類型的完整性，應在呼叫預存程序之前初始化輸入/輸出參數，或應指定所需的 PHPTYPE。 如需指定 PHPTYPE 的相關資訊，請參閱 [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md)。  
  
由於預存程序會傳回兩個結果，因此 [sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md) 必須在預存程序執行完成之後呼叫，輸出參數的值才可供使用。 在呼叫 **sqlsrv_next_result** 之後，*$vacationHrs* 會包含預存程序所傳回的輸出參數值。  
  
> [!NOTE]  
> 使用標準語法呼叫預存程序，是建議的做法。 如需標準語法的詳細資訊，請參閱[呼叫預存程序](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)。  
  
此範例假設本機電腦上已安裝 SQL Server 和 [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) 資料庫。 從命令列執行範例時，所有輸出都會寫入至主控台。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Drop the stored procedure if it already exists. */  
$tsql_dropSP = "IF OBJECT_ID('SubtractVacationHours', 'P') IS NOT NULL  
                DROP PROCEDURE SubtractVacationHours";  
$stmt1 = sqlsrv_query( $conn, $tsql_dropSP);  
if( $stmt1 === false )  
{  
     echo "Error in executing statement 1.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Create the stored procedure. */  
$tsql_createSP = "CREATE PROCEDURE SubtractVacationHours  
                        @EmployeeID int,  
                        @VacationHrs smallint OUTPUT  
                  AS  
                  UPDATE HumanResources.Employee  
                  SET VacationHours = VacationHours - @VacationHrs  
                  WHERE EmployeeID = @EmployeeID;  
                  SET @VacationHrs = (SELECT VacationHours  
                                      FROM HumanResources.Employee  
                                      WHERE EmployeeID = @EmployeeID)";  
  
$stmt2 = sqlsrv_query( $conn, $tsql_createSP);  
if( $stmt2 === false )  
{  
     echo "Error in executing statement 2.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*--------- The next few steps call the stored procedure. ---------*/  
  
/* Define the Transact-SQL query. Use question marks (?) in place of  
the parameters to be passed to the stored procedure */  
$tsql_callSP = "{call SubtractVacationHours( ?, ?)}";  
  
/* Define the parameter array. By default, the first parameter is an  
INPUT parameter. The second parameter is specified as an INOUT  
parameter. Initializing $vacationHrs to 8 sets the returned PHPTYPE to  
integer. To ensure data type integrity, output parameters should be  
initialized before calling the stored procedure, or the desired  
PHPTYPE should be specified in the $params array.*/  
  
$employeeId = 4;  
$vacationHrs = 8;  
$params = array(   
                 array($employeeId, SQLSRV_PARAM_IN),  
                 array(&$vacationHrs, SQLSRV_PARAM_INOUT)  
               );  
  
/* Execute the query. */  
$stmt3 = sqlsrv_query( $conn, $tsql_callSP, $params);  
if( $stmt3 === false )  
{  
     echo "Error in executing statement 3.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Display the value of the output parameter $vacationHrs. */  
sqlsrv_next_result($stmt3);  
echo "Remaining vacation hours: ".$vacationHrs;  
  
/*Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_free_stmt( $stmt3);  
sqlsrv_close( $conn);  
?>  
```  

> [!NOTE]
> 時的輸入/輸出參數繫結至一個 bigint 型別，如果值可能超出範圍的最後[整數](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)，您必須指定 SQLSRV_SQLTYPE_BIGINT SQL 欄位類型。 否則，它可能會導致 「 超出範圍的值 」 例外狀況。

## <a name="example-2"></a>範例 2
此程式碼範例示範如何將大型的 bigint 值，做為輸入/輸出參數繫結。  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"testDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Assume the stored procedure spTestProcedure exists, which retrieves a bigint value of some large number
// e.g. 9223372036854
$bigintOut = 0;
$outSql = "{CALL spTestProcedure (?)}";
$stmt = sqlsrv_prepare($conn, $outSql, array(array(&$bigintOut, SQLSRV_PARAM_INOUT, null, SQLSRV_SQLTYPE_BIGINT)));
sqlsrv_execute($stmt);
echo "$bigintOut\n";   // Expect 9223372036854

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```

## <a name="see-also"></a>另請參閱  
[如何：使用 SQLSRV 驅動程式指定參數方向](../../connect/php/how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)

[如何：使用 SQLSRV 驅動程式擷取輸出參數](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)

[擷取資料](../../connect/php/retrieving-data.md)  
  
