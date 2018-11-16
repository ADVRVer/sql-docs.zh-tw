---
title: PDOStatement::bindValue |Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 13bc4ece-420e-4887-8809-bf0705ddf126
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7ae069a5bb485f4b74a11b066f5871aba2f30ec
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606278"
---
# <a name="pdostatementbindvalue"></a>PDOStatement::bindValue
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

將值繫結至 SQL 陳述式中的具名或問號預留位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
bool PDOStatement::bindValue($parameter, $value[, $data_type]);  
```  
  
#### <a name="parameters"></a>參數  
$*parameter*：(混合的) 參數識別碼。 若是使用具名預留位置的陳述式，使用參數名稱 (:name)。 若是使用問號語法的已備妥陳述式，則是以 1 起始之索引的參數。
  
$*value*：要繫結至參數的 (混合) 值。  
  
$*data_type*：PDO::PARAM_* 常數所表示的選用 (整數) 資料類型。 預設值是 PDO::PARAM_STR。  
  
## <a name="return-value"></a>傳回值  
如果成功，則為 TRUE，否則為 FALSE。  
  
## <a name="remarks"></a>Remarks  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]2.0 版已加入 PDO 支援。  
  
## <a name="example"></a>範例  
此範例說明在繫結 $contact 的值之後，變更值並不會使傳入查詢中的值隨之變更。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindValue(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindValue(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```

> [!NOTE]
> 建議使用字串做為輸入，繫結至的值時[十進位或數值資料行](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql)若要確保精確性與正確性，如 PHP 有限精確度[浮點數](https://php.net/manual/en/language.types.float.php)。 這同樣適用於 bigint 資料行，尤其是值為範圍外[整數](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)。

## <a name="example"></a>範例  
此程式碼範例示範如何繫結十進位值做為輸入參數。  

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
$stmt->bindValue(1, $input, PDO::PARAM_STR);
$stmt->execute();
```
  
## <a name="see-also"></a>另請參閱  
[PDOStatement 類別](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
