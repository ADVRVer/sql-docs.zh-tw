---
title: PDOStatement::getColumnMeta
description: Microsoft PDO_SQLSRV Driver for PHP for SQL Server 中的 PDOStatement::getColumnMeta 函式適用的 API 參考。
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c92a21cc-8e53-43d0-a4bf-542c77c100c9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e29418276e6209f669ae57160809120d61e19a05
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645073"
---
# <a name="pdostatementgetcolumnmeta"></a>PDOStatement::getColumnMeta
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

擷取資料行的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
  
array PDOStatement::getColumnMeta ( $column );  
```  
  
#### <a name="parameters"></a>參數  
*$conn*：(整數) 您要擷取其中繼資料的資料行號碼 (以零起始)。  
  
## <a name="return-value"></a>傳回值  
包含資料行中繼資料的關聯陣列 (索引鍵和值)。 如需陣列中欄位的描述，請參閱＜備註＞一節。  
  
## <a name="remarks"></a>備註  
下表將描述 getColumnMeta 所傳回陣列中的欄位。  
  
|名稱|VALUES|  
|--------|----------|  
|native_type|指定資料行的 PHP 類型。 一定是字串。|  
|driver:decl_type|指定用來表示資料庫中的資料行值的 SQL 類型。 如果結果集內的資料行是函數的結果，則此值不是由 PDOStatement::getColumnMeta 傳回。|  
|flags|指定為此資料行設定的旗標。 一律是 0。|  
|NAME|指定資料庫中資料行的名稱。|  
|table|指定包含資料庫中資料行的資料表名稱。 永遠為空白。|  
|len|指定資料行長度。|  
|精確度|指定此資料行的數值有效位數。|  
|pdo_type|指定此資料行的類型 (以 PDO::PARAM_* 常數表示)。 一律是 PDO::PARAM_STR (2)。|  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]2.0 版已加入 PDO 支援。  
  
## <a name="example"></a>範例  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$stmt = $conn->query("select * from Person.ContactType");  
$metadata = $stmt->getColumnMeta(2);  
var_dump($metadata);  
  
print $metadata['sqlsrv:decl_type'] . "\n";  
print $metadata['native_type'] . "\n";  
print $metadata['name'];  
?>  
```  
  
## <a name="sensitivity-data-classification-metadata"></a>敏感性資料分類中繼資料

從 5.8.0 版開始，新的陳述式屬性 `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` 可供使用者透過使用 `PDOStatement::getColumnMeta` (其需要 Microsoft ODBC Driver 17.4.2 或更新版本) 來存取 Microsoft SQL Server 2019 中的[敏感性資料分類中繼資料](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-ver15&tabs=t-sql#subheading-4)。

請注意，`PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` 屬性預設為 `false`，但當設定為 `true` 時，先前所提到的陣列欄位 `flags` 將會填入敏感性資料分類中繼資料 (如果其存在的話)。 

以患者資料表為例：

```
CREATE TABLE Patients 
      [PatientId] int identity,
      [SSN] char(11),
      [FirstName] nvarchar(50),
      [LastName] nvarchar(50),
      [BirthDate] date)
```

我們可以將 SSN 和 BirthDate 資料行分類，如下所示：

```
ADD SENSITIVITY CLASSIFICATION TO [Patients].SSN WITH (LABEL = 'Highly Confidential - secure privacy', INFORMATION_TYPE = 'Credentials')
ADD SENSITIVITY CLASSIFICATION TO [Patients].BirthDate WITH (LABEL = 'Confidential Personal Data', INFORMATION_TYPE = 'Birthdays')
```

若要存取中繼資料，請在將 `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` 設定為 true 之後使用 `PDOStatement::getColumnMeta`，如下列程式碼片段中所示：

```
$options = array(PDO::SQLSRV_ATTR_DATA_CLASSIFICATION => true);
$tableName = 'Patients';
$tsql = "SELECT * FROM $tableName";
$stmt = $conn->prepare($tsql, $options);
$stmt->execute();
$numCol = $stmt->columnCount();

for ($i = 0; $i < $numCol; $i++) {
    $metadata = $stmt->getColumnMeta($i);
    $jstr = json_encode($metadata);
    echo $jstr . PHP_EOL;
}
```

針對所有資料行的中繼資料輸出為：

```
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"int identity","native_type":"string","table":"","pdo_type":2,"name":"PatientId","len":10,"precision":0}
{"flags":{"Data Classification":[{"Label":{"name":"Highly Confidential - secure privacy","id":""},"Information Type":{"name":"Credentials","id":""}}]},"sqlsrv:decl_type":"char","native_type":"string","table":"","pdo_type":2,"name":"SSN","len":11,"precision":0}
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"FirstName","len":50,"precision":0}
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"LastName","len":50,"precision":0}
{"flags":{"Data Classification":[{"Label":{"name":"Confidential Personal Data","id":""},"Information Type":{"name":"Birthdays","id":""}}]},"sqlsrv:decl_type":"date","native_type":"string","table":"","pdo_type":2,"name":"BirthDate","len":10,"precision":0}
```

如果我們透過將 `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` 設定為 `false` (預設案例) 來修改上述程式碼片段，`flags` 欄位將和先前一樣一律會是 `0`，如下所示：

```
{"flags":0,"sqlsrv:decl_type":"int identity","native_type":"string","table":"","pdo_type":2,"name":"PatientId","len":10,"precision":0}
{"flags":0,"sqlsrv:decl_type":"char","native_type":"string","table":"","pdo_type":2,"name":"SSN","len":11,"precision":0}
{"flags":0,"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"FirstName","len":50,"precision":0}
{"flags":0,"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"LastName","len":50,"precision":0}
{"flags":0,"sqlsrv:decl_type":"date","native_type":"string","table":"","pdo_type":2,"name":"BirthDate","len":10,"precision":0}
```

      
## <a name="see-also"></a>另請參閱  
[PDOStatement 類別](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
