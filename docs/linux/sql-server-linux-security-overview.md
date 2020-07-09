---
title: Linux 上的 SQL Server 安全性限制
description: 本文描述 Linux 上的 SQL Server 限制。
author: VanMSFT
ms.author: vanto
ms.date: 09/12/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: f1820b54532a820a47babdaf79e28d1baa0f096b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895302"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Linux 上的 SQL Server 安全性限制

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Linux 上的 SQL Server 目前有下列限制：

* 提供標準密碼原則。 MUST_CHANGE 是您可以設定的唯一選項。 不支援 CHECK_POLICY 選項。
* 不支援可延伸金鑰管理。 
* 不支援使用儲存在 Azure Key Vault 中的金鑰。
* SQL Server 會產生自己的自我簽署憑證以加密連線。 您可以設定 SQL Server 以利用使用者提供的 TLS 憑證。 

如需 SQL Server 中可用的安全性功能詳細資訊，請參閱 [SQL Server 資料庫引擎和 Azure SQL Database 的資訊安全中心](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)。

## <a name="next-steps"></a>後續步驟

如需常見的安全性工作，請參閱[開始使用 Linux 上的 SQL Server 安全性功能](sql-server-linux-security-get-started.md)。 如需變更 TCP 通訊埠號碼、SQL Server 目錄及設定追蹤旗標或定序的指令碼，請參閱[使用 mssql-conf 在 Linux 上設定 SQL Server](sql-server-linux-configure-mssql-conf.md)。
