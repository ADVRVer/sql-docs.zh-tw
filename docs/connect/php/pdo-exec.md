---
title: 'Pdo:: exec |Microsoft 文件'
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
ms.topic: conceptual
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2cc8fbe7b6795452b7d41009c3830e162aa80af
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="pdoexec"></a>PDO::exec
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

傳回陳述式所影響的資料列數目，以準備及執行單一函數呼叫中的 SQL 陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
  
int PDO::exec ($statement)  
```  
  
#### <a name="parameters"></a>參數  
*$statement*：一個字串，包含要執行的 SQL 陳述式。  
  
## <a name="return-value"></a>傳回值  
一個整數，報告受影響的資料列數目。  
  
## <a name="remarks"></a>備註  
如果 *$statement* 包含多個 SQL 陳述式，則只會針對最後一個陳述式報告受影響的資料列計數。  
  
PDO::exec 不會傳回 SELECT 陳述式的結果。  
  
以下是會影響 PDO::exec 行為的屬性：  
  
-   PDO::ATTR_DEFAULT_FETCH_MODE  
  
-   PDO::SQLSRV_ATTR_ENCODING  
  
-   PDO::SQLSRV_ATTR_QUERY_TIMEOUT  
  
如需詳細資訊，請參閱 [PDO::setAttribute](../../connect/php/pdo-setattribute.md)。 
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]2.0 版已加入 PDO 支援。  
  
## <a name="example"></a>範例  
此範例會刪除 Table1 中在 col1 中有 'xxxyy' 的資料列。 接著，範例會報告已刪除的資料列數目。  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec("use Test");  
   $ret = $c->exec("delete from Table1 where col1 = 'xxxyy'");  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[PDO 類別](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
