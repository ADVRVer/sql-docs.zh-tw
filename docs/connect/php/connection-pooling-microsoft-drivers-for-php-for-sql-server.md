---
title: 連接共用 (Microsoft Drivers for PHP for SQL Server)
ms.custom: ''
ms.date: 07/10/2017
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
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a332153e4e2651079198dac5b4390c3b56d550d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MTE
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>連接共用 (Microsoft Drivers for PHP for SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

以下是對於 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]中的連接共用所須注意的相關要點：  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 會使用 ODBC 連接共用。  
  
-   依預設會啟用連接共用。 在 Linux 和 Mac OS X 中，只有當 ODBC 連接共用已啟用共用連接。 當連接共用已啟用，連線到伺服器，此驅動程式會嘗試使用共用連接，然後再建立一個新。 如果在集區中找不到等同的連接，則會建立新連接，並加入至集區。 驅動程式會根據連接字串的比較，來判斷連接是否相等。  
  
-   使用來自集區的連接時，連接狀態會重設。  
  
-   關閉連接會將連接傳回集區。  
  
如需連接共用的詳細資訊，請參閱 [驅動程式管理員連接共用](../../odbc/reference/develop-app/driver-manager-connection-pooling.md)。  
  
## <a name="enablingdisabling-connection-pooling"></a>啟用/停用連接共用
### <a name="windows"></a>Windows
您可以將連接字串中的 **ConnectionPooling** 屬性值設為 false 或 0，以強制驅動程式建立新連接 *而不是在連接集區中尋找相同的連接*。  
  
如果在連接字串中省略 *ConnectionPooling* 屬性，或是將該屬性設為 **true** 或 1，則只有在連接集區中沒有相同的連接存在時，驅動程式才會建立新的連接。  
  
如需其他連接屬性的相關資訊，請參閱 [Connection Options](../../connect/php/connection-options.md)。  
### <a name="linux-and-mac-os-x"></a>Linux 和 Mac OS X
*ConnectionPooling*屬性不能啟用/停用連接共用。 

連接共用可以是啟用/停用透過編輯 odbcinst.ini 組態檔。 驅動程式應重新載入，變更才會生效。

設定`Pooling`至`Yes`和正`CPTimeout`odbcinst.ini 中的值會啟用連接共用。 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
設定`Pooling`至`No`在 odbcinst.ini 中會強制驅動程式建立新的連接。
```
[ODBC]
Pooling=No
```
  
## <a name="see-also"></a>另請參閱  
[如何：使用 Windows 驗證進行連線](../../connect/php/how-to-connect-using-windows-authentication.md)

[如何：使用 SQL Server 驗證進行連線](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  
