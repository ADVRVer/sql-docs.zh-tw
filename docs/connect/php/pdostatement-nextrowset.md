---
title: 'Pdostatement:: Nextrowset |Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 048a6d8f-7fc4-449e-8161-19268c68f41d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6982660f0a10cd4c92bf2b7e4ef7c0102779c58c
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601808"
---
# <a name="pdostatementnextrowset"></a>PDOStatement::nextRowset
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

將資料指標移至下一個結果集。  
  
## <a name="syntax"></a>語法  
  
```  
  
bool PDOStatement::nextRowset();  
```  
  
## <a name="return-value"></a>傳回值  
成功時傳回 true，否則傳回 false。  
  
## <a name="remarks"></a>Remarks  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]2.0 版已加入 PDO 支援。  
  
## <a name="example"></a>範例  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $query1 = "select * from Person.Address where City = 'Bothell';";  
   $query2 = "select * from Person.ContactType;";  
  
   $stmt = $conn->query( $query1 . $query2 );  
  
   $rowset1 = $stmt->fetchAll();  
   $stmt->nextRowset();  
   $rowset2 = $stmt->fetchAll();  
   var_dump( $rowset1 );  
   var_dump( $rowset2 );  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[PDOStatement 類別](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
