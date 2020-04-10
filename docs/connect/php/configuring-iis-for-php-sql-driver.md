---
title: 為 Microsoft Drivers for PHP for SQL Server 設定 IIS | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- configuring, Internet Information Services
ms.assetid: d2dc75d3-9bf7-481c-85f2-8b6310b21461
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31d46254f153742ff3923aa2484872aedb7cf077
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907334"
---
# <a name="configuring-iis-for-the-microsoft-drivers-for-php-for-sql-server"></a>為 Microsoft Drivers for PHP for SQL Server 設定 IIS
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

本主題提供 [Internet Information Services (IIS) 網站](https://www.iis.net/)上與設定 IIS 以裝載 PHP 應用程式相關的資源連結。 此處列出的資源特別適合搭配使用 FastCGI 與 IIS。 FastCGI 是標準通訊協定，可讓應用程式架構的通用閘道介面 (CGI) 可執行檔得以與 Web 伺服器互動。 FastCGI 不同於標準 CGI 通訊協定，FastCGI 會將 CGI 處理序重複使用於多個要求。  
  
## <a name="tutorials"></a>教學課程  
下列連結是有關設定適用於 PHP 的 FastCGI 以及在 IIS 6.0 和 IIS 7.0 上裝載 PHP 應用程式的教學課程：  
  
-   [FastCGI 與 PHP](https://docs.microsoft.com/iis/web-hosting/web-server-for-shared-hosting/fastcgi-with-php)  
-   [使用 FastCGI 在 IIS 7.0 上裝載 PHP 應用程式](https://docs.microsoft.com/iis/application-frameworks/install-and-configure-php-applications-on-iis/using-fastcgi-to-host-php-applications-on-iis)  
-   [使用 FastCGI 在 IIS 6.0 上裝載 PHP 應用程式](https://docs.microsoft.com/iis/application-frameworks/install-and-configure-php-applications-on-iis/using-fastcgi-to-host-php-applications-on-iis-60)  
-   [設定 IIS 6.0 的 FastCGI 延伸模組](https://docs.microsoft.com/iis/application-frameworks/install-and-configure-php-on-iis/configuring-the-fastcgi-extension-for-iis-60)  
  
## <a name="video-presentations"></a>視訊簡報  
下列連結是有關設定適用於 PHP 的 FastCGI 以及使用 IIS 7.0 功能來裝載 PHP 應用程式的視訊簡報：  
  
-   [設定適用於 PHP 的 FastCGI](https://docs.microsoft.com/iis/application-frameworks/running-php-applications-on-iis/set-up-fastcgi-for-php)  
-   [在 Microsoft Internet Information Services 7 上與 PHP 合作](https://docs.microsoft.com/iis/application-frameworks/running-php-applications-on-iis/mix08-partying-with-php-on-microsoft-internet-information-services-7-and-above)  
  
## <a name="support-resources"></a>支援資源  
下列論壇提供有關 IIS 的 FastCGI 社群支援：  
  
-   [FastCGI 處理常式](https://forums.iis.net/1103.aspx)  
-   [IIS 7 - FastCGI 模組](https://forums.iis.net/1104.aspx)  
  
## <a name="see-also"></a>另請參閱  
[開始使用 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Microsoft Drivers for PHP for SQL Server 的程式設計指南](../../connect/php/programming-guide-for-php-sql-driver.md)

[SQLSRV 驅動程式 API 參考](../../connect/php/sqlsrv-driver-api-reference.md)

[常數 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
  
