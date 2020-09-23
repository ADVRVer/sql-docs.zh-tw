---
title: PDOStatement::fetch
description: Microsoft PDO_SQLSRV Driver for PHP for SQL Server 中的 PDOStatement::fetch 函式適用的 API 參考。
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4368e362-5bda-4da1-8462-33714683c39f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 338d871e7e0cbbfa2da04d04d33fe672f85d8083
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645105"
---
# <a name="pdostatementfetch"></a>PDOStatement::fetch
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

從結果集內擷取資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
mixed PDOStatement::fetch ([ $fetch_style[, $cursor_orientation[, $cursor_offset]]] );  
```  
  
#### <a name="parameters"></a>參數  
$*fetch_style*：選擇性 (整數) 符號，用於指定資料列資料的格式。 如需 $*fetch_style* 的可能值清單，請參閱＜備註＞一節。 預設值為 PDO::FETCH_BOTH。提取方法中的  $*fetch_style* 會覆寫 PDO::query 方法中指定的 $*fetch_style*。  
  
$*cursor_orientation*：選擇性 (整數) 符號，指出在準備陳述式指定 `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL` 時所要擷取的資料列。 如需 $*cursor_orientation* 的可能值清單，請參閱＜備註＞一節。 如需使用可捲動資料指標的範例，請參閱 [PDO::prepare](../../connect/php/pdo-prepare.md) 。  
  
$*cursor_offset*：選擇性 (整數) 符號，指定在 $*cursor_orientation* 為 PDO::FETCH_ORI_ABS 或 PDO::FETCH_ORI_REL，且 PDO::ATTR_CURSOR 為 PDO::CURSOR_SCROLL 時所要提取的資料列。  
  
## <a name="return-value"></a>傳回值  
傳回資料列或 false 的混合值。  
  
## <a name="remarks"></a>備註  
在呼叫提取時，資料指標會自動前進。 下表包含可能的 $*fetch_style* 值清單。  
  
|$*fetch_style*|描述|  
|-------------------|---------------|  
|PDO::FETCH_ASSOC|指定依資料行名稱編製索引的陣列。|  
|PDO::FETCH_BOTH|指定依資料行名稱且以 0 起始而編製索引的陣列。 此為預設值。|  
|PDO::FETCH_BOUND|會傳回 true，並指定 [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md)所指定的值。|  
|PDO::FETCH_CLASS|建立執行個體，並將資料行對應至具名屬性。<br /><br />在呼叫提取之前呼叫 [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) 。|  
|PDO::FETCH_INTO|重新整理要求類別的執行個體。<br /><br />在呼叫提取之前呼叫 [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) 。|  
|PDO::FETCH_LAZY|建立存取期間的變數名稱，並建立未命名的物件。|  
|PDO::FETCH_NUM|指定依照以 0 起始的資料行順序編製索引的陣列。|  
|PDO::FETCH_OBJ|以對應至資料行名稱的屬性名稱，指定未命名的物件。|  
  
如果資料指標位於結果集的結尾 (已擷取最後一個資料列，且資料指標已越過結果集界限)，且資料指標是順向的 (PDO::ATTR_CURSOR = PDO::CURSOR_FWDONLY)，後續的提取呼叫將會失敗。  
  
如果資料指標是可捲動的 (PDO::ATTR_CURSOR = PDO::CURSOR_SCROLL)，則提取會在結果集界限內移動資料指標。 下表包含可能的 $*cursor_orientation* 值清單。  
  
|$*cursor_orientation*|描述|  
|--------------------------|---------------|  
|PDO::FETCH_ORI_NEXT|擷取下一個資料列。 此為預設值。|  
|PDO::FETCH_ORI_PRIOR|擷取上一個資料列。|  
|PDO::FETCH_ORI_FIRST|擷取第一個資料列。|  
|PDO::FETCH_ORI_LAST|擷取最後一個資料列。|  
|PDO::FETCH_ORI_ABS, *num*|依資料列號碼擷取在 $*cursor_offset* 中要求的資料列。|  
|PDO::FETCH_ORI_REL, *num*|依目前位置的相對位置，擷取在 $*cursor_offset* 中要求的資料列。|  
  
如果為 $*cursor_offset* 或 $*cursor_orientation* 所指定的值導致位置超出結果集界限，則提取將會失敗。  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]2.0 版已加入 PDO 支援。  
  
## <a name="example"></a>範例  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print( "\n---------- PDO::FETCH_CLASS -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg";  
      }  
  
      function __toString() {  
         return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
      }  
   }  
  
   $stmt->setFetchMode(PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
   while ( $row = $stmt->fetch(PDO::FETCH_CLASS)) {   
      print($row . "\n");   
   }  
  
   print( "\n---------- PDO::FETCH_INTO -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
   $c_obj = new cc( '' );  
  
   $stmt->setFetchMode(PDO::FETCH_INTO, $c_obj);  
   while ( $row = $stmt->fetch(PDO::FETCH_INTO)) {   
      echo "$c_obj\n";  
   }  
  
   print( "\n---------- PDO::FETCH_ASSOC -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_ASSOC );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_NUM -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_NUM );  
   print_r ($result );  
  
   print( "\n---------- PDO::FETCH_BOTH -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_BOTH );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_LAZY -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_LAZY );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_OBJ -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_OBJ );  
   print $result->Name;  
   print( "\n \n" );  
  
   print( "\n---------- PDO::FETCH_BOUND -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->bindColumn('Name', $name);  
   $result = $stmt->fetch( PDO::FETCH_BOUND );  
   print $name;  
   print( "\n \n" );  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[PDOStatement 類別](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
