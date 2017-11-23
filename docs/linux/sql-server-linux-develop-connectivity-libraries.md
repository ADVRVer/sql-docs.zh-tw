---
title: "連接程式庫和架構 |Microsoft 文件"
description: "列出用戶端應用程式可以使用從各種不同的語言來連線到 Microsoft SQL Server 在內部部署或雲端，在 Linux、 Windows 或 Docker 和 Azure SQL Database 和 Azure SQL 資料倉儲中的連線能力驅動程式。"
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.workload: Inactive
ms.openlocfilehash: 765fb054ab4fb5332df7b2f9d2e202188f621b67
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>連接程式庫和適用於 Microsoft SQL Server 的架構

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

請查看我們[快速入門教學課程](http://aka.ms/sqldev)快速開始使用程式設計語言如 C#、 Java、 Node.js、 PHP 以及 Python 和建置在 Linux 或 Windows Docker macOS 上使用 SQL Server 的應用程式。

下表列出的連接程式庫或*驅動程式*用戶端應用程式可以使用從各種不同的語言連接到並使用 Microsoft SQL Server 在內部部署或雲端，在 Linux、 Windows 或 Docker 和 Azure SQL Database 和 Azure SQL 資料倉儲中。 

| 語言 | 平台 | 其他資源 | 下載 | 開始使用 |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows、 Linux、 macOS | [Microsoft ADO.NET for SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [下載](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [快速入門](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows、 Linux、 macOS | [Microsoft JDBC Driver for SQL Server](http://msdn.microsoft.com/library/mt484311.aspx) | [下載](http://go.microsoft.com/fwlink/?LinkId=245496) |  [快速入門](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows、 Linux、 macOS| [SQL Server 的 PHP SQL 驅動程式](http://msdn.microsoft.com/library/dn865013.aspx) | 作業系統： <br/> \*[Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \*[Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \*[macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [快速入門](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows、 Linux、 macOS | [Node.js Driver for SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [快速入門](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows、 Linux、 macOS | [Python SQL 驅動程式](../connect/python/python-driver-for-sql-server.md) <br/> \*[pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [快速入門](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows、 Linux、 macOS | [適用於 SQL Server 的 Ruby 驅動程式](../connect/ruby/ruby-driver-for-sql-server.md) | [快速入門](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows、 Linux、 macOS | [Microsoft ODBC Driver for SQL Server](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) | [下載](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) |  

下表列出物件關聯式對應 (ORM) 架構和 web 架構用戶端應用程式可以使用與 Microsoft SQL Server 在內部部署執行，或在雲端中，在 Linux、 Windows 或 Docker 和 Azure SQL Database 和 Azure SQL 資料倉儲的一些的範例。 

| 語言 | 平台 | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows、 Linux、 macOS | [Entity Framework](https://docs.microsoft.com/en-us/ef)<br>[Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/index) |
| Java | Windows、 Linux、 macOS |[休眠 ORM](http://hibernate.org/orm)|
| PHP | Windows、 Linux | [Laravel （最具有說服力）](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows、 Linux、 macOS | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | Windows、 Linux、 macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows、 Linux、 macOS | [Ruby 滑軌上](http://rubyonrails.org/) |

## <a name="related-links"></a>相關連結
- [SQL Server 驅動程式](http://msdn.microsoft.com/library/mt654049.aspx)連接從用戶端應用程式
