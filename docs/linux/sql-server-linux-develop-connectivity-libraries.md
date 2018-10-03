---
title: 連線程式庫和架構 |Microsoft Docs
description: 列出用戶端應用程式可以使用從各種不同的語言來連線到內部部署上執行的 Microsoft SQL Server，或在雲端、 Linux、 Windows 或 Docker 和 Azure SQL Database 和 Azure SQL 資料倉儲中的連線能力驅動程式。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.openlocfilehash: a650d85bbd4865e839cdf486020baff759b50bac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819876"
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>連線程式庫和 Microsoft SQL server 的架構

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

請參閱[開始使用教學課程](http://aka.ms/sqldev)快速開始使用程式設計語言，例如 C#、 Java、 Node.js、 PHP 和 Python，並建置應用程式在 macOS 上使用 Linux 或 Windows 或 Docker 上的 SQL Server。

下表列出連線程式庫或*驅動程式*用戶端應用程式可以從各種不同的語言來連線至並使用 Microsoft SQL Server 執行內部部署或在雲端、 Linux、 Windows 或 Docker 上使用和也為 Azure SQL Database 和 Azure SQL 資料倉儲。 

| 語言 | 平台 | 其他資源 | 下載 | 開始使用 |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows、 Linux、 macOS | [Microsoft ADO.NET for SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [下載](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [開始使用](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows、 Linux、 macOS | [Microsoft JDBC Driver for SQL Server](http://msdn.microsoft.com/library/mt484311.aspx) | [下載](http://go.microsoft.com/fwlink/?LinkId=245496) |  [開始使用](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows、 Linux、 macOS| [PHP SQL Driver for SQL Server](../connect/php/microsoft-php-driver-for-sql-server.md) | 作業系統： <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [開始使用](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows、 Linux、 macOS | [Node.js Driver for SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [開始使用](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows、 Linux、 macOS | [Python SQL 驅動程式](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [開始使用](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows、 Linux、 macOS | [適用於 SQL Server 的 Ruby 驅動程式](../connect/ruby/ruby-driver-for-sql-server.md) | [開始使用](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows、 Linux、 macOS | [Microsoft ODBC Driver for SQL Server](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) | [下載](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) |  

下表列出一些物件關聯式對應 (ORM) 架構和 web 架構的用戶端應用程式可以使用內部部署上執行的 Microsoft SQL server，或在雲端、 Linux、 Windows 或 Docker 和 Azure SQL database 中的範例和Azure SQL 資料倉儲。 

| 語言 | 平台 | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows、 Linux、 macOS | [Entity Framework](https://docs.microsoft.com/ef)<br>[Entity Framework Core](https://docs.microsoft.com/ef/core/index) |
| Java | Windows、 Linux、 macOS |[休眠 ORM](http://hibernate.org/orm)|
| PHP | Windows、 Linux | [Laravel （導師）](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows、 Linux、 macOS | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | Windows、 Linux、 macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows、 Linux、 macOS | [Ruby on Rails](http://rubyonrails.org/) |

## <a name="related-links"></a>相關連結
- [SQL Server 驅動程式](http://msdn.microsoft.com/library/mt654049.aspx)從用戶端應用程式連線
