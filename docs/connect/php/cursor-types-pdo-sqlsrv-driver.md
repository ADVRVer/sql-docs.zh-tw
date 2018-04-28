---
title: 資料指標類型 （PDO_SQLSRV 驅動程式） |Microsoft 文件
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
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fef4910ae38fba0d101e95e9f7ad0c73d4541b72
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-types-pdosqlsrv-driver"></a>資料指標類型 （PDO_SQLSRV 驅動程式）
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO_SQLSRV 驅動程式可讓您建立具有數個資料指標的其中一個可捲動的結果集。  
  
如需有關如何指定資料指標使用 PDO_SQLSRV 驅動程式資訊和程式碼範例，請參閱[pdo:: prepare](../../connect/php/pdo-prepare.md)。  
  
## <a name="pdosqlsrv-and-server-side-cursors"></a>PDO_SQLSRV 和伺服器端資料指標  
3.0 版之前[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]，PDO_SQLSRV 驅動程式可讓您建立含伺服器端順向或靜態資料指標的結果集。 從 3.0 版開始[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]，keyset 和 dynamic 資料指標也會提供。  
  
您可以使用 pdo:: prepare 或 pdostatement:: Setattribute 來選取其中一種資料指標類型，表示伺服器端資料指標的類型：  
  
-   PDO:: ATTR_CURSOR = &GT; PDO:: CURSOR_FWDONLY  
  
-   PDO:: ATTR_CURSOR = &GT; PDO:: CURSOR_SCROLL  
  
要求 keyset 或 dynamic 資料指標，您可以指定 pdo:: ATTR_CURSOR = > pdo:: CURSOR_SCROLL，然後再傳遞適當的值以 pdo:: SQLSRV_ATTR_CURSOR_SCROLL_TYPE。 您可以將它傳遞至 pdo:: SQLSRV_ATTR_CURSOR_SCROLL_TYPE 的可能值為：  
  
-   PDO::SQLSRV_CURSOR_BUFFERED  
  
-   PDO::SQLSRV_CURSOR_DYNAMIC  
  
-   PDO::SQLSRV_CURSOR_KEYSET_DRIVEN  
  
-   PDO::SQLSRV_CURSOR_STATIC  
  
## <a name="pdosqlsrv-and-client-side-cursors"></a>PDO_SQLSRV 和用戶端資料指標  
3.0 版中所加入的用戶端資料指標[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]，可讓您快取的整個結果集在記憶體中。 其中一個優點是，資料列計數可用之後執行的查詢。  
  
用戶端資料指標應該用於小型-至中型的結果集。 大型結果集應該使用伺服器端資料指標。  
  
查詢會傳回 false，如果緩衝區不夠大到足以包含的整個結果集時使用的用戶端資料指標。 您可以增加緩衝區大小超過 PHP 記憶體限制。  
  
您可以設定的保留結果集的 PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE 屬性的緩衝區大小[pdo:: setattribute](../../connect/php/pdo-setattribute.md)或[pdostatement:: Setattribute](../../connect/php/pdostatement-setattribute.md)。 您也可以設定最大緩衝區大小 pdo_sqlsrv.client_buffer_max_kb_size php.ini 檔案中 (例如，pdo_sqlsrv.client_buffer_max_kb_size = 1024年)。  
  
您表示您想要使用 pdo:: prepare 或 pdostatement:: Setattribute 的用戶端資料指標，並選取 pdo:: ATTR_CURSOR = > pdo:: CURSOR_SCROLL 資料指標類型。  您接著可以指定 pdo:: SQLSRV_ATTR_CURSOR_SCROLL_TYPE = > PDO::SQLSRV_CURSOR_BUFFERED。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED));  
$stmt->execute();  
print $stmt->rowCount();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[指定資料指標類型及選取資料列](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)  
  
