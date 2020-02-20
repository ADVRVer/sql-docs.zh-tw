---
title: Microsoft Drivers for PHP for SQL Server 的版本資訊 | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: v-dapugl, kenvh
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5e279ba446e790a2262e5f0effe160632065dcba
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76941213"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Microsoft Drivers for PHP for SQL Server 的版本資訊

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

此頁面討論每版 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 的新功能。  

<!--
Hello, We are standardizing the format of content inside our Release Notes (or What's New) articles.
Instead of bullets (or paragraphs), we have shifted to the 2-column format you see for H2 **What's New in Version 5.6**.
It is not necessary to reformat all the older H2 sections in this Release Notes file, but.....

Going forward, please be sure to use the 2-column format.

Also, all Release Notes .md file names now must begin with 'release-notes-*.md'.  And no filler words.
The 5.6 edition of this file is being renamed.....
FROM:  'release-notes-for-the-php-sql-driver.md'
TO  :  'release-notes-php-sql-driver.md'

For any questions, ask GeneMi or CraigG.
Thanks a lot.  2019-03-28  (DevO= 1467988)
-->

## <a name="whats-new-in-version-58"></a>5\.8 版的新功能

| 新項目 | 詳細資料 |
| :------- | :------ |
| 已新增 PHP 7.4 的支援。 | &nbsp; |
| 已停止 PHP 7.1 的支援。 | &nbsp; |
| 已在所有平台上新增 Microsoft ODBC Driver 17.5 的支援。 | &nbsp; |
| 已新增 Debian 10 和 Red Hat 8 的支援。 | 兩者都需要 ODBC Driver 17.4 或更新版本。 |
| 已新增 macOS Catalina、Alpine Linux 3.11<sup>1</sup> 和 Ubuntu 19.10 的支援。 | 全部都需要 ODBC Driver 17.5 或更新版本。 |
| 已停止 SQL Server 2008 R2、macOS Sierra、Ubuntu 18.10 和 Ubuntu 19.04 的支援。 | &nbsp; |
| 當連線到 SQL Server 時，支援「語言」選項。 | &nbsp; |
| PHP 7.2 中導入 PHP 延伸字串類型的支援。 | &nbsp; |
| 「資料分類」敏感度中繼資料擷取的支援。 | 需要 SQL Server 2019 和 ODBC Driver 17.4.2 或更新版本。 |
| 具有安全記憶體保護區的 Always Encrypted 支援。 | 需要 ODBC Driver 17.4 或更新版本。 |
| Linux 與 macOS 中地區設定可設定選項的支援。 |
| 已藉由在擷取時快取中繼資料，以及忽略多餘呼叫來改善效能。 | &nbsp; |
| &nbsp; | &nbsp; |

<sup>1</sup> 5.8 版的 Alpine Linux 支援是實驗性的。

## <a name="whats-new-in-version-56"></a>5\.6 版的新功能

| 新項目 | 詳細資料 |
| :------- | :------ |
| PHP 7.3 的支援。 | &nbsp; |
| 已停止 PHP 7.0 的支援。 | &nbsp; |
| 所有平台上 Microsoft ODBC Driver 17.3 的支援。 | &nbsp; |
| macOS Mojave 的支援。 | 需要 ODBC Driver 17.3 或更新版本。 |
| Ubuntu 18.10 和 Suse Linux 15 的支援。 | 兩者都需要 ODBC Driver 17.3 或更新版本。 |
| 已停止 Linux Ubuntu 17.10 和 macOS El Capitan 的支援。 | &nbsp; |
| Azure AD 存取權杖的支援。 | 在 Linux 和 macOS 中，需要 ODBC Driver 17.2+ 和 unixODBC 2.3.6+。 |
| 針對 Azure 資源使用受控識別對 Azure AD 進行驗證的支援。 | 需要 ODBC Driver 17.3+。 |
| 新的擷取功能 | &bull; &nbsp; pdo_sqlsrv 的新 PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE 旗標，可將日期時間作為物件傳回。<br/><br/>&bull; &nbsp; 針對 sqlsrv 將 ReturnDatesAsStrings 選項新增至陳述式層級。<br/><br/>&bull; &nbsp; 針對兩個驅動程式新增連線與陳述式層級選項，可對擷取結果中的小數值進行格式設定。 |
| 如果使用者選擇從來源建置，則支援驅動程式的靜態編譯。 | &nbsp; |
| 已藉由在擷取時快取中繼資料，以及加快 Unicode 字串轉換來改善效能。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>5\.3 版的新功能

- 所有平台上 Microsoft ODBC Driver 17.2 的支援
- macOS High Sierra 的支援 (需要 ODBC Driver 17 和更新版本)
- 針對基本 CRUD 功能支援適用於 Always Encrypted 的 Azure Key Vault，讓所有支援的 Windows、Linux 或 macOS 平台都能使用 Always Encrypted 功能 [搭配 PHP Drivers for SQL Server 使用 Always Encrypted](../../connect/php/using-always-encrypted-php-drivers.md)
- 支援 Ubuntu 18.04 LTS (需要 ODBC Driver 17.2)
- Linux 以及 macOS 中連線復原的支援 (需要 ODBC Driver 17.2)

## <a name="whats-new-in-version-52"></a>5\.2 版的新功能

- Windows 上 PHP 7.2.1 和更新版本，以及其他平台上 7.2.0 和更新版本的支援
- Microsoft ODBC Driver 17 的支援
  - 17 版現在是所有平台上的預設值
- Ubuntu 17.10、Debian 9 和 Suse Enterprise Linux 12 的支援
- 已停止 Ubuntu 15.10 的支援
- Windows 上 Always Encrypted (具有 CRUD 功能) 的支援。 如需詳細資訊，請參閱[搭配 PHP Drivers for SQL Server 使用 Always Encrypted](../../connect/php/using-always-encrypted-php-drivers.md)
  - Windows 憑證存放區的支援
  - Microsoft ODBC Driver 17 和更新版本才支援 Always Encrypted
- Linux 和 macOS 上非 UTF8 地區設定的支援
  - Microsoft ODBC Driver 17 和更新版本才支援 Linux 和 macOS 上的非 UTF8 地區設定
- Azure SQL 資料倉儲的支援
- Azure SQL 受控執行個體的支援

## <a name="whats-new-in-version-43"></a>4\.3 版的新功能

- PHP 7.1 的支援
- macOS Sierra 和 macOS El Capitan 的支援
- Ubuntu 15.10 和 Debian 8 的支援
- 已停止 Ubuntu 15.04 的支援
- 透過透明網路 IP 解析支援 Always On 可用性群組。 如需詳細資訊，請參閱 [Connection Options](../../connect/php/connection-options.md)。
- 新增 sql_variant 資料類型有限制的支援。
- Windows 中的「閒置連線復原」功能支援。 如需詳細資訊，請參閱 [Connection Options](../../connect/php/connection-options.md)。
- Linux 和 macOS 的連線共用支援。 如需詳細資訊，請參閱[連接共用](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)。
- 使用 ActiveDirectoryPassword 和 SqlPassword 進行 Azure Active Directory 驗證的支援。 如需詳細資訊，請參閱 [Connection Options](../../connect/php/connection-options.md)。

## <a name="whats-new-in-version-40"></a>4\.0 版的新功能

- PHP 7.0 的支援  
- 完整 64 位元支援
- Ubuntu 15.04、Ubuntu 16.04 和 RedHat 7 的支援

## <a name="whats-new-in-version-32"></a>3\.2 版的新功能

- PHP 5.6 的支援   
- 包含 PHP 舊有的 5.5 和 5.4 版最新的更新   
- 需要 Microsoft ODBC Driver 11 for SQL Server  

## <a name="whats-new-in-version-31"></a>3\.1 版的新功能

- PHP 5.5 的支援  
- 需要 Microsoft ODBC Driver 11 for SQL Server。 舊版需要 SQL Native Client。  

## <a name="whats-new-in-version-30"></a>3\.0 版的新功能  

- PHP 5.4 的支援  [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]第 3 版不支援 PHP 5.2。  
- 已加入 AttachDBFileName 連接選項。 如需詳細資訊，請參閱 [Connection Options](../../connect/php/connection-options.md)。  
- LocalDB 的支援，已在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中新增。 如需詳細資訊，請參閱[支援 LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)。
- 已加入 AttachDBFileName 連接選項。 如需詳細資訊，請參閱 [Connection Options](../../connect/php/connection-options.md)。  
- 高可用性與災害復原功能的支援。 如需詳細資訊，請參閱[對於高可用性、災害復原的支援](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。
- 用戶端資料指標的支援 (快取記憶體中的結果集)。 如需詳細資訊，請參閱[資料指標類型 &#40;SQLSRV 驅動程式&#41;](../../connect/php/cursor-types-sqlsrv-driver.md) 和[資料指標類型 &#40;PDO_SQLSRV 驅動程式&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)。
- 已加入 PDO::ATTR_EMULATE_PREPARES 屬性。 如需詳細資訊，請參閱 [PDO::prepare](../../connect/php/pdo-prepare.md)。  

## <a name="whats-new-in-version-20"></a>2\.0 版的新功能

在 2.0 版中，已加入對 PDO_SQLSRV 驅動程式的支援。 如需詳細資訊，請參閱 [PDO_SQLSRV 驅動程式參考](../../connect/php/pdo-sqlsrv-driver-reference.md)。  

## <a name="see-also"></a>另請參閱

[Microsoft Drivers for PHP for SQL Server 概觀](../../connect/php/overview-of-the-php-sql-driver.md)
