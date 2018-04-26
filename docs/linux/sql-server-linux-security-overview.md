---
title: SQL Server on Linux 的安全性限制 |Microsoft 文件
description: 本文描述 SQL Server Linux 的限制。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.workload: Inactive
ms.openlocfilehash: dbf964ea466522b5735c8ccac85821ca1e1426c4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="security-limitations-for-sql-server-on-linux"></a>SQL Server on Linux 的安全性限制

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

在 Linux 上的 SQL Server 目前有下列限制：

* 提供標準的密碼原則。 MUST_CHANGE 是唯一可設定的選項。  
* 不支援 「 可延伸金鑰管理。 
* 不支援使用儲存在 Azure 金鑰保存庫金鑰。
* SQL Server 會產生自己的自我簽署的憑證來加密連線。 SQL Server 可以設定為使用提供的 TLS 憑證的使用者。 

如需 SQL Server 中可用的安全性功能的詳細資訊，請參閱[SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)。

## <a name="next-steps"></a>後續的步驟

如需常見的安全性工作，請參閱[開始使用 Linux 上的 SQL Server 安全性功能](sql-server-linux-security-get-started.md)。 指令碼來變更 TCP 連接埠號碼，SQL Server 目錄中，並設定 traceflag 或定序，請參閱[設定 SQL Server on Linux 與 mssql conf](sql-server-linux-configure-mssql-conf.md)。
