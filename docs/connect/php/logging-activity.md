---
title: 記錄活動 |Microsoft 文件
ms.custom: ''
ms.date: 03/26/2018
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
- logging activity
ms.assetid: a777b3d9-2262-4e82-bc82-b62ad60d0e55
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec9c672009668d8320380dd6163de7e5ccc61270
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="logging-activity"></a>記錄活動
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

依預設不會記錄 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 所產生的錯誤和警告。 本主題討論如何設定記錄活動。  
  
## <a name="logging-activity-using-the-pdosqlsrv-driver"></a>使用 PDO_SQLSRV 驅動程式記錄活動  
唯一適用於 PDO_SQLSRV 驅動程式的組態，是 php.ini 檔案中的 pdo_sqlsrv.log_severity 項目。  
  
在 php.ini 檔案的結尾加入下列項目：  
  
```  
[pdo_sqlsrv]  
pdo_sqlsrv.log_severity = <number>  
```  
  
**log_severity** 可以是下列其中一個值：  
  
|Value|설명|  
|---------|---------------|  
|0|停用記錄 (這是沒有任何定義時的預設值)。|  
|-1|指定記錄錯誤、 警告和通知。|  
|1|指定錯誤記錄。|  
|2|指定也會記錄警告。|  
|4|指定會記錄通知。|  
  
記錄資訊會加入至 phperrors.log 檔案。  
  
PHP 會在初始化時讀取組態檔，並將資料儲存在快取中；它也提供 API，以更新這些設定並立即使用，再寫入至組態檔。 此 API 讓應用程式指令碼即使在 PHP 初始化之後仍可變更設定。  
  
## <a name="logging-activity-using-the-sqlsrv-driver"></a>使用 SQLSRV 驅動程式記錄活動  
若要開啟記錄功能，您可以使用[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)函式，或是修改 php.ini 檔案。 您可以記錄初始化、連接、陳述式或錯誤函數的活動。 您也可以指定是要記錄錯誤、警告、通知，還是三者全部記錄。  
  
> [!NOTE]  
> 您可以在 php.ini 檔案中設定記錄檔的位置。  
  
### <a name="turning-logging-on"></a>開啟記錄  
您可以藉由開啟記錄[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)函式以指定的值**LogSubsystems**設定。 例如，下列程式碼行會將驅動程式設定為要記錄連接的活動：  
  
`sqlsrv_configure("LogSubsystems", SQLSRV_LOG_SYSTEM_CONN);`  
  
下表說明可做為 **LogSubsystems** 設定值的常數：  
  
|值 (括號中的整數對等項目)|Description|  
|-----------------------------------------------|---------------|  
|SQLSRV_LOG_SYSTEM_ALL (-1)|開啟所有子系統的記錄。|  
|SQLSRV_LOG_SYSTEM_OFF (0)|關閉記錄。 這是預設值。|  
|SQLSRV_LOG_SYSTEM_INIT (1)|開啟初始化活動的記錄。|  
|SQLSRV_LOG_SYSTEM_CONN (2)|開啟連接活動的記錄。|  
|SQLSRV_LOG_SYSTEM_STMT (4)|開啟陳述式活動的記錄。|  
|SQLSRV_LOG_SYSTEM_UTIL (8)|開啟錯誤函數活動 (例如 handle_error 和 handle_warning) 的記錄。|  
  
您可以設定多個值同時為**LogSubsystems**使用邏輯 OR 運算子 (|) 設定。 例如，下列程式碼行會同時開啟連接和陳述式活動的記錄：  
  
`sqlsrv_configure("LogSubsystems", SQLSRV_LOG_SYSTEM_CONN | SQLSRV_LOG_SYSTEM_STMT);`  
  
您也可以開啟記錄功能藉由指定的整數值**LogSubsystems**設定在 php.ini 檔案中。 例如，將下列這一行加入`[sqlsrv]`區段 php.ini 檔案的開啟連接活動的記錄：  
  
`sqlsrv.LogSubsystems = 2`  
  
將整數值相加，可以同時指定多個選項。 例如，將下列這一行加入`[sqlsrv]`區段 php.ini 檔案的開啟連接和陳述式活動的記錄：  
  
`sqlsrv.LogSubsystems = 6`  
  
### <a name="logging-errors-warnings-and-notices"></a>記錄錯誤、警告和通知  
開啟記錄之後，您必須指定要記錄的項目。 您可以記錄下列一或多項：錯誤、警告和通知。 例如，下列程式碼行指定只要警告也會記錄：  
  
`sqlsrv_configure("LogSeverity", SQLSRV_LOG_SEVERITY_WARNING);`  
  
> [!NOTE]  
> 預設設定**LogSeverity**是**SQLSRV_LOG_SEVERITY_ERROR**。 如果記錄已開啟，但未指定 **LogSeverity** 的設定，將只會記錄錯誤。  
  
下表說明可做為 **LogSeverity** 設定值的常數：  
  
|值 (括號中的整數對等項目)|Description|  
|-----------------------------------------------|---------------|  
|SQLSRV_LOG_SEVERITY_ALL (-1)|指定記錄錯誤、 警告和通知。|  
|SQLSRV_LOG_SEVERITY_ERROR (1)|指定錯誤記錄。 這是預設值。|  
|SQLSRV_LOG_SEVERITY_WARNING (2)|指定也會記錄警告。|  
|SQLSRV_LOG_SEVERITY_NOTICE (4)|指定會記錄通知。|  
  
您可以設定多個值同時為**LogSeverity**使用邏輯 OR 運算子 (|) 設定。 例如，下列程式碼行會指定要記錄錯誤和警告：  
  
`sqlsrv_configure("LogSeverity", SQLSRV_LOG_SEVERITY_ERROR | SQLSRV_LOG_SEVERITY_WARNING);`  
  
> [!NOTE]  
> 指定的值**LogSeverity**設定不會開啟記錄。 您必須開啟記錄功能藉由指定的值**LogSubsystems**設定，然後指定設定值的記錄項目的嚴重性**LogSeverity**。  
  
您也可以在 php.ini 檔案中使用整數值，以指定 **LogSeverity** 設定。 例如，將下列這一行加入至 php.ini 檔案的 `[sqlsrv]` 區段，將只會啟用警告的記錄：  
  
`sqlsrv.LogSeverity = 2`  
  
將整數值相加，可以同時指定多個選項。 例如，將下列這一行加入`[sqlsrv]`php.ini 檔案的區段會啟用記錄錯誤和警告：  
  
`sqlsrv.LogSeverity = 3`  
  
## <a name="see-also"></a>另請參閱  
[程式程式設計指南 Microsoft Drivers for PHP，適用於 SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[常數 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)

[sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md)

[SQLSRV 驅動程式 API 參考](../../connect/php/sqlsrv-driver-api-reference.md)  
  
