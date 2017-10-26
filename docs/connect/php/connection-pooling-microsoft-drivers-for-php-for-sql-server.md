---
title: "連接共用 (Microsoft Drivers for PHP for SQL Server) |Microsoft 文件"
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e536bbaee8f9dd934f24504e8c1226c9db7db9de
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>連接共用 (Microsoft Drivers for PHP for SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

以下是對於 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]中的連接共用所須注意的相關要點：  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 會使用 ODBC 連接共用。  
  
-   根據預設，在 Windows 中啟用連接共用。 在 Linux 和 Mac OS X 中，只有當 ODBC 連接共用已啟用共用連接。 當連接共用已啟用，連線到伺服器，此驅動程式會嘗試使用共用連接，然後再建立一個新。 如果在集區中找不到等同的連接，則會建立新連接，並加入至集區。 驅動程式會根據連接字串的比較，來判斷連接是否相等。  
  
-   使用來自集區的連接時，連接狀態會重設。  
  
-   關閉連接會將連接傳回集區。  
  
如需連接共用的詳細資訊，請參閱 [驅動程式管理員連接共用](http://go.microsoft.com/fwlink/?linkid=119622)。  
  
## <a name="enablingdisabling-connection-pooling"></a>啟用/停用連接共用
### <a name="windows"></a>Windows
您可以強制驅動程式所設定的值建立新的連接 （而不是相同的連接，連接集區中尋找） *ConnectionPooling*中的連接字串屬性**false** （或 0）。  
  
如果*ConnectionPooling*省略從連接字串屬性，或者如果它設定為**true** （或 1） 驅動程式才會建立新的連接中沒有相同的連接連接集區。  
  
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
[如何：使用 Windows 驗證進行連接](../../connect/php/how-to-connect-using-windows-authentication.md)  
[如何：使用 SQL Server 驗證進行連接](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  

