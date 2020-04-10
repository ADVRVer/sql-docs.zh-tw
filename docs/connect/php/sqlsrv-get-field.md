---
title: sqlsrv_get_field | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_get_field
apitype: NA
helpviewer_keywords:
- sqlsrv_get_field
- API Reference, sqlsrv_get_field
- retrieving data, as a single field
ms.assetid: fa17cc56-fb38-433b-a40d-65642f04dc23
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9770d24fc810860088f853a2effaadd8d125ab22
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922742"
---
# <a name="sqlsrv_get_field"></a>sqlsrv_get_field
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

從目前資料列的指定欄位擷取資料。 欄位資料必須依序存取。 例如，第一個欄位的資料不可在已存取第二個欄位的資料之後存取。  
  
## <a name="syntax"></a>語法  
  
```  
sqlsrv_get_field( resource $stmt, int $fieldIndex [, int $getAsType])  
```  
  
#### <a name="parameters"></a>參數  
*$stmt*：對應至執行之陳述式的陳述式資源。  
  
*$fieldIndex*：要擷取之欄位的索引。 索引從零開始。  
  
*$getAsType* [選擇性]：**SQLSRV** 常數 (**SQLSRV_PHPTYPE_&#x2a;** )，可決定傳回資料的 PHP 資料類型。 如需支援之資料類型的資訊，請參閱[常數 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)。 若未指定傳回類型，將會傳回預設 PHP 類型。 如需關於預設 PHP 類型的詳細資訊，請參閱 [Default PHP Data Types](../../connect/php/default-php-data-types.md)。 如需如何指定 PHP 資料類型的詳細資訊，請參閱[如何：指定 PHP 資料類型](../../connect/php/how-to-specify-php-data-types.md)。  
  
## <a name="return-value"></a>傳回值  
欄位資料。 您可以使用 *$getAsType* 參數，指定傳回資料的 PHP 資料類型。 若未指定傳回資料類型，將會傳回預設 PHP 資料類型。 如需關於預設 PHP 類型的詳細資訊，請參閱 [Default PHP Data Types](../../connect/php/default-php-data-types.md)。 如需如何指定 PHP 資料類型的詳細資訊，請參閱[如何：指定 PHP 資料類型](../../connect/php/how-to-specify-php-data-types.md)。  
  
## <a name="remarks"></a>備註  
結合 **sqlsrv_fetch** 和 **sqlsrv_get_field**，可提供僅限轉送的資料存取。  
  
結合 **sqlsrv_fetch**/**sqlsrv_get_field**，會僅將結果集資料列的一個欄位載入指令碼記憶體中，並允許指定 PHP 傳回類型。 (如需關於如何指定 PHP 傳回類型的詳細資訊，請參閱[如何：指定 PHP 資料類型](../../connect/php/how-to-specify-php-data-types.md)。)函數的此一組合，也可讓您以串流的形式擷取資料。 (如需以資料流形式擷取資料的資訊，請參閱[使用 SQLSRV 驅動程式以資料流形式擷取資料](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)。)  
  
## <a name="example"></a>範例  
下列範例會擷取包含產品評論和評論者名稱的資料列。 若要從結果集內擷取資料，請使用 **sqlsrv_get_field**。 此範例假設本機電腦上已安裝 SQL Server 和 [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) 資料庫。 從命令列執行範例時，所有輸出都會寫入至主控台。  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up and execute the query. Note that both ReviewerName and  
Comments are of the SQL Server nvarchar type. */  
$tsql = "SELECT ReviewerName, Comments   
         FROM Production.ProductReview  
         WHERE ProductReviewID=1";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Make the first row of the result set available for reading. */  
if( sqlsrv_fetch( $stmt ) === false )  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Note: Fields must be accessed in order.  
Get the first field of the row. Note that no return type is  
specified. Data will be returned as a string, the default for  
a field of type nvarchar.*/  
$name = sqlsrv_get_field( $stmt, 0);  
echo "$name: ";  
  
/*Get the second field of the row as a stream.  
Because the default return type for a nvarchar field is a  
string, the return type must be specified as a stream. */  
$stream = sqlsrv_get_field( $stmt, 1,   
                            SQLSRV_PHPTYPE_STREAM( SQLSRV_ENC_CHAR));  
while( !feof( $stream))  
{   
    $str = fread( $stream, 10000);  
    echo $str;  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[SQLSRV 驅動程式 API 參考](../../connect/php/sqlsrv-driver-api-reference.md)  

[擷取資料](../../connect/php/retrieving-data.md)  

[關於文件中的程式碼範例](../../connect/php/about-code-examples-in-the-documentation.md)  
  
