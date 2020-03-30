---
title: 預設 PHP 資料類型 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: b66c301d-3d20-45b8-a112-225d8f01c0bd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11026bcb372759f62aa0b0d5f406a6721b65c135
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993674"
---
# <a name="default-php-data-types"></a>預設 PHP 資料類型
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

從伺服器擷取資料時，如果使用者尚未指定任何 PHP 資料類型，則 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 會將資料轉換成預設 PHP 資料類型。  
  
使用 PDO_SQLSRV 驅動程式傳回資料時，資料類型會是 int 或 string。  
  
本主題的其餘部分將討論使用 SQLSRV 驅動程式的預設資料類型。  
  
下表列出 SQL Server 資料類型 (從伺服器擷取的資料類型)、預設 PHP 資料類型 (資料會轉換成的資料類型)，以及資料流和字串的預設編碼。 如需從伺服器擷取資料時如何指定資料類型的詳細資訊，請參閱[如何：指定 PHP 資料類型](../../connect/php/how-to-specify-php-data-types.md)。  
  
|SQL Server 類型|預設 PHP 類型|預設編碼|  
|-------------------|--------------------|--------------------|  
|BIGINT|String|8 位元字元<sup>1</sup>|  
|BINARY|資料流<sup>2</sup>|二進位<sup>3</sup>|  
|bit|整數|8 位元字元<sup>1</sup>|  
|char|String|8 位元字元<sup>1</sup>|  
|date<sup>4</sup>|Datetime|不適用|  
|datetime<sup>4</sup>|Datetime|不適用|  
|datetime2<sup>4</sup>|Datetime|不適用|  
|datetimeoffset<sup>4</sup>|Datetime|不適用|  
|decimal|String|8 位元字元<sup>1</sup>|  
|FLOAT|Float|8 位元字元<sup>1</sup>|  
|geography|資料流|二進位<sup>3</sup>|  
|幾何|資料流|二進位<sup>3</sup>|  
|image<sup>5</sup>|資料流<sup>2</sup>|二進位<sup>3</sup>|  
|int|整數|8 位元字元<sup>1</sup>|  
|money|String|8 位元字元<sup>1</sup>|  
|NCHAR|String|8 位元字元<sup>1</sup>|  
|NUMERIC|String|8 位元字元<sup>1</sup>|  
|NVARCHAR|String|8 位元字元<sup>1</sup>|  
|nvarchar(MAX)|資料流<sup>2</sup>|8 位元字元<sup>1</sup>|  
|ntext<sup>6</sup>|資料流<sup>2</sup>|8 位元字元<sup>1</sup>|  
|real|Float|8 位元字元<sup>1</sup>|  
|smalldatetime|Datetime|8 位元字元<sup>1</sup>|  
|SMALLINT|整數|8 位元字元<sup>1</sup>|  
|SMALLMONEY|String|8 位元字元<sup>1</sup>|  
|sql_variant<sup>7</sup>|String|8 位元字元<sup>1</sup>|  
|text<sup>8</sup>|資料流<sup>2</sup>|8 位元字元<sup>1</sup>|  
|time<sup>4</sup>|Datetime|不適用|  
|timestamp|String|8 位元字元<sup>1</sup>|  
|TINYINT|整數|8 位元字元<sup>1</sup>|  
|UDT|資料流<sup>2</sup>|二進位<sup>3</sup>|  
|UNIQUEIDENTIFIER|String<sup>9</sup>|8 位元字元<sup>1</sup>|  
|varbinary|資料流<sup>2</sup>|二進位<sup>3</sup>|  
|varbinary(MAX)|資料流<sup>2</sup>|二進位<sup>3</sup>|  
|varchar|String|8 位元字元<sup>1</sup>|  
|varchar(MAX)|資料流<sup>2</sup>|8 位元字元<sup>1</sup>|
|Xml|資料流<sup>2</sup>|8 位元字元<sup>1</sup>|  
  

1.  資料會以如同在系統上設定之 Windows 地區設定的字碼頁中指定的 8 位元字元傳回。 系統會以單一位元組問號 (?) 字元取代任何多位元組字元或未對應到此字碼頁的字元。  
  
2.  如果 [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) 或 [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) 用來擷取預設 PHP 類型為「資料流」的資料，會以字串形式 (其編碼方式與資料流相同) 傳回資料。 例如，如果使用 **sqlsrv_fetch_array** 擷取 SQL Server 二進位類型，則預設傳回型別會是二進位字串。  
  
3.  資料會以原始位元組資料流形式從伺服器傳回，而不需執行編碼或轉譯。  

4.  可以字串形式擷取日期和時間。 如需詳細資訊，請參閱[如何：使用 SQLSRV 驅動程式以字串形式擷取日期和時間類型](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)。  

5.  這是對應至 varbinary(max) 類型的傳統類型。

6. 這是對應至 nvarchar(max) 類型的傳統類型。

7.  雙向或輸出參數中不支援 sql_variant。

8.  這是對應至 varchar(max) 類型的傳統類型。  
  
9.  UNIQUEIDENTIFIER 是下列規則運算式所代表的 GUID：  
  
    [0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-f]{4}-[0-9a-fA-f]{4}-[0-9a-fA-F]{12}  
 
 
## <a name="other-new-sql-server-2008-data-types-and-features"></a>其他新的 SQL Server 2008 資料類型和功能  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 不支援 SQL Server 2008 的新資料類型，以及存在於資料行 (例如資料表值參數) 之外的資料類型。 下表摘要說明 SQL Server 2008 新功能的 PHP 支援。  
  
|功能|PHP 支援|  
|-----------|---------------|  
|資料表值參數|否|  
|疏鬆資料行|部分|  
|Null 位元壓縮|是|  
|大型 CLR 使用者定義型別 (UDT)|是|  
|服務主體名稱|否|  
|MERGE|是|  
|FILESTREAM|部分|  
  
部分類型支援表示您無法以程式設計方式查詢資料行的類型。  
  
## <a name="see-also"></a>另請參閱  
[常數 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[轉換資料類型](../../connect/php/converting-data-types.md)

[PHP 類型](https://php.net/manual/en/language.types.php)

[資料類型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  
