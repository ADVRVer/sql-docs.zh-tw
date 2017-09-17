---
title: "預設 SQL Server 資料類型 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b71a28f48cdbfe9e70079abfc392f53976c90c87
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="default-sql-server-data-types"></a>預設 SQL Server 資料類型
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

將資料傳送至伺服器時，如果使用者未指定 SQL Server 資料類型，則 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 會將資料從 PHP 資料類型轉換成 SQL Server 資料類型。 下表列出 PHP 資料類型 (要傳送至伺服器的資料類型) 和預設 SQL Server 資料類型 (資料會轉換成的資料類型)。 如需在將資料傳送至伺服器時如何指定資料類型的詳細資訊，請參閱 [如何：使用 SQLSRV 驅動程式指定 SQL Server 資料類型](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md)。  
  
|PHP 資料類型|SQLSRV 驅動程式中的預設 SQL Server 類型|PDO_SQLSRV 驅動程式中的預設 SQL Server 類型|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|不支援|  
|布林|bit|bit|  
|Integer|int|int|  
|Float|float(24)|不支援|  
|字串 (長度小於 8000 個位元組)|varchar (<string length>)|varchar (<string length>)|  
|字串 (長度大於 8000 個位元組)|varchar(max)|varchar(max)|  
|資源|不支援。|不支援。|  
|資料流 (編碼：不是二進位)|varchar(max)|varchar(max)|  
|資料流 (編碼：二進位)|varbinary|varbinary|  
|Array|不支援。|不支援。|  
|物件|不支援。|不支援。|  
|DateTime (1)|datetime|不支援。|  
  
## <a name="see-also"></a>另請參閱  
[常數 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Converting Data Types](../../connect/php/converting-data-types.md)  
[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
[PHP 類型](http://go.microsoft.com/fwlink/?LinkId=109071)  
[資料類型 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=109068)  
  

