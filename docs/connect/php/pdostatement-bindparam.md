---
title: 'Pdostatement:: Bindparam |Microsoft 文件'
ms.custom: ''
ms.date: 04/11/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2a351fa6e916d37c38e2ed3beb1cea8190183e7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

將參數繫結至 SQL 陳述式中的具名或問號預留位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
bool PDOStatement::bindParam($parameter, &$variable[, $data_type[, $length[, $driver_options]]]);  
```  
  
#### <a name="parameters"></a>參數  
$*參數*: （混合） 參數識別碼。 陳述式，使用具名預留位置，使用參數名稱 (: name)。 使用問號語法的已備妥陳述式，它是以 1 起始的索引參數。  
  
&$*變數*： 要繫結至 SQL 陳述式參數之 PHP 變數的 （混合） 名稱。  
  
$*data_type*： 選用 （整數） pdo:: PARAM_ * 常數。 預設值是 PDO::PARAM_STR。  
  
$*長度*: 選用 （整數） 資料類型長度。 您可以指定 pdo:: SQLSRV_PARAM_OUT_DEFAULT_SIZE 指出 $ 中使用 pdo:: PARAM_INT 或 pdo:: PARAM_BOOL 時的預設大小*data_type*。  
  
$*driver_options*： 選用 （混合） 驅動程式特有的選項。 例如，您可以指定 PDO::SQLSRV_ENCODING_UTF8，以 UTF-8 編碼的字串形式將資料行繫結至變數。  
  
## <a name="return-value"></a>傳回值  
如果成功，則為 TRUE，否則為 FALSE。  
  
## <a name="remarks"></a>備註  
當 null 資料繫結至類型 varbinary、 binary 或 varbinary （max） 的伺服器資料行應該指定二進位編碼 (pdo:: SQLSRV_ENCODING_BINARY) 使用 $*driver_options*。 如需編碼常數的詳細資訊，請參閱[常數](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)。  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]2.0 版已加入 PDO 支援。  

## <a name="example"></a>範例  
此程式碼範例說明在 $contact 繫結至參數之後，變更值並將會使傳入查詢中的值隨之變更。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>範例  
此程式碼範例說明如何存取輸出參數。  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(*) from Sys.tables");  
$stmt->bindParam(1, $input1, PDO::PARAM_STR, 10);  
$stmt->execute();  
echo $input1;  
?>  
```  
  
> [!NOTE]
> Bigint 型別，繫結 output 參數，如果值可能會超出範圍時[整數](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)，pdo:: PARAM_INT 使用 pdo:: SQLSRV_PARAM_OUT_DEFAULT_SIZE，可能會導致 「 超出範圍的值 」 例外狀況。 因此，請改用 default pdo:: PARAM_STR，並提供結果的字串，最多為 21 的大小。 它是數字，包括任何 bigint 值的負值正負號的數目上限。 

## <a name="example"></a>範例  
此程式碼範例說明如何使用輸入/輸出參數。  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  

> [!NOTE]
> 建議使用字串做為輸入，當繫結至值[十進位或數值資料行](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)為確保如 PHP 有限的有效位數的有效位數和精確度[浮點數](http://php.net/manual/en/language.types.float.php)。

## <a name="example"></a>範例  
此程式碼範例示範如何將繫結十進位值做為輸入參數。  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```


## <a name="see-also"></a>另請參閱  
[PDOStatement 類別](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
