---
title: PDOStatement::closeCursor |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8997ab61-e948-4d54-8d32-fc080d55525c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: de023c9bdd452a4611d28493b37f2a2046d485fe
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MTE
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="pdostatementclosecursor"></a>PDOStatement::closeCursor
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

關閉資料指標，使陳述式能夠再次執行。  
  
## <a name="syntax"></a>語法  
  
```  
  
bool PDOStatement::closeCursor();  
```  
  
## <a name="return-value"></a>傳回值  
如果成功，則為 true，否則為 false。  
  
## <a name="remarks"></a>Remarks  
當 MultipleActiveResultSets 連接選項設為 false 時，closeCursor 會有效用。  如需 MultipleActiveResultSets 連接選項的詳細資訊，請參閱[如何：停用 Multiple Active Resultsets ](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)MARS。  
  
您也可以不要呼叫 closeCursor，而僅將陳述式控制代碼設為 Null。  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]2.0 版已加入 PDO 支援。  
  
## <a name="example"></a>範例  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets' => false ) );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
$stmt2 = $conn->prepare('SELECT * FROM HumanResources.Department');  
  
$stmt->execute();  
  
$result = $stmt->fetch();  
print_r($result);  
  
$stmt->closeCursor();  
  
$stmt2->execute();  
$result = $stmt2->fetch();  
print_r($result);  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[PDOStatement 類別](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
