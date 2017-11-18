---
title: "sqlsrv_execute |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_execute
apitype: NA
helpviewer_keywords:
- sqlsrv_exclude
- executing queries
- API Reference, sqlsrv_execute
ms.assetid: 38331bc2-4391-4f9f-aa83-9873dad605a0
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d9326e49d0fd22440fe8d974d7d0b66800e04cdc
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvexecute"></a>sqlsrv_execute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

執行先前已備妥的陳述式。 如需關於準備執行陳述式的詳細資訊，請參閱 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) 。  
  
> [!NOTE]  
> 此函數非常適合用來以不同的參數值執行備妥的陳述式多次。  
  
## <a name="syntax"></a>語法  
  
```  
  
sqlsrv_execute( resource $stmt)  
```  
  
#### <a name="parameters"></a>參數  
*$stmt*：指定要執行之陳述式的資源。 如需如何建立陳述式資源的詳細資訊，請參閱 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)。  
  
## <a name="return-value"></a>傳回值  
一個布林值：如果陳述式成功執行，則為 **true** 。 否則為 **false**。  
  
## <a name="example"></a>範例  
下列範例會執行一個陳述式，以更新 *AdventureWorks* 資料庫之 [Sales.SalesOrderDetail](http://go.microsoft.com/fwlink/?LinkID=67739) 資料表中的欄位。 此範例假設本機電腦上已安裝 SQL Server 和 AdventureWorks 資料庫。 從命令列執行範例時，所有輸出都會寫入至主控台。  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ( ?)   
         WHERE SalesOrderDetailID = ( ?)";  
  
/* Set up the parameters array. Parameters correspond, in order, to  
question marks in $tsql. */  
$params = array( 5, 10);  
  
/* Create the statement. */  
$stmt = sqlsrv_prepare( $conn, $tsql, $params);  
if( $stmt )  
{  
     echo "Statement prepared.\n";  
}  
else  
{  
     echo "Error in preparing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Execute the statement. Display any errors that occur. */  
if( sqlsrv_execute( $stmt))  
{  
      echo "Statement executed.\n";  
}  
else  
{  
     echo "Error in executing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[SQLSRV 驅動程式 API 參考](../../connect/php/sqlsrv-driver-api-reference.md)  
[關於文件中的程式碼範例](../../connect/php/about-code-examples-in-the-documentation.md)  
[sqlsrv_query](../../connect/php/sqlsrv-query.md)  
  

