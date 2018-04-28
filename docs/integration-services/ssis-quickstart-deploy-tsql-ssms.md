---
title: 使用 Transact-SQL 部署 SSIS 專案 (SSMS) | Microsoft Docs
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 65991b38dfecff6a57b9fba0343b43307ec9c2fc
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="deploy-an-ssis-project-from-ssms-with-transact-sql"></a>使用 Transact-SQL 從 SSMS 部署 SSIS 專案

本快速入門示範如何使用 SQL Server Management Studio (SSMS) 連線至 SSIS 目錄資料庫，然後使用 Transact-SQL 陳述式將 SSIS 專案部署至 SSIS 目錄。 

> [!NOTE]
> 使用 SSMS 連線至 Azure SQL Database 伺服器時，無法使用本文中所述的方法。 `catalog.deploy_project` 預存程序必須有本機 (內部部署) 檔案系統中 `.ispac` 檔案的路徑。

SQL Server Management Studio 是整合式環境，用於管理任何 SQL 基礎結構，從 SQL Sever 到 SQL Database 皆適用。 如需 SSMS 的詳細資訊，請參閱 [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)。

## <a name="prerequisites"></a>Prerequisites

開始之前，請確定您有最新版的 SQL Server Management Studio。 若要下載 SSMS，請參閱[下載 SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)。

## <a name="connect-to-the-ssis-catalog-database"></a>連線至 SSIS 目錄資料庫

使用 SQL Server Management Studio，以建立與 SSIS 目錄的連線。 

> [!NOTE]
> Azure SQL Database 伺服器會接聽連接埠 1433。 如果您要嘗試透過公司防火牆連線至 Azure SQL Database 伺服器，則必須在公司防火牆中開啟此連接埠，讓您成功連線。

1. 開啟 SQL Server Management Studio。

2. 在 [連線至伺服器] 對話方塊中，輸入下列資訊：

   | 設定       | 建議值 | 其他資訊 | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **伺服器類型** | 資料庫引擎 | 這是必要的值。 |
   | **伺服器名稱** | 完整伺服器名稱 |  |
   | **驗證** | SQL Server 驗證 | 本快速入門使用 SQL 驗證。 |
   | **登入** | 伺服器系統管理員帳戶 | 這是您在建立伺服器時指定的帳戶。 |
   | **密碼** | 伺服器系統管理員帳戶的密碼 | 這是您在建立伺服器時指定的密碼。 |

3. 按一下 **[連接]**。 [物件總管] 視窗會在 SSMS 中開啟。 

4. 在 [物件總管] 中，展開 [Integration Services 目錄]，然後展開 [SSISDB] 以檢視 SSIS 目錄資料庫中的物件。

## <a name="run-the-t-sql-code"></a>執行 T-SQL 程式碼
執行下列 Transact-SQL 程式碼來部署 SSIS 專案。

1.  在 SSMS 中，開啟新的查詢視窗，並貼入下列程式碼。

2.  更新 `catalog.deploy_project` 預存程序中您系統的參數值。

3.  確定 SSISDB 是目前的資料庫。

4.  執行指令碼。

5. 在 [物件總管] 中，於必要時更新 **SSISDB** 的內容，然後檢查是否有您所部署的專案。

```sql
DECLARE @ProjectBinary AS varbinary(max)
DECLARE @operation_id AS bigint
SET @ProjectBinary =
    (SELECT * FROM OPENROWSET(BULK '<project_file_path>.ispac', SINGLE_BLOB) AS BinaryData)

EXEC catalog.deploy_project @folder_name = '<target_folder>',
    @project_name = '<project_name',
    @Project_Stream = @ProjectBinary,
    @operation_id = @operation_id out
```

## <a name="next-steps"></a>後續步驟
- 請考慮使用其他方式來部署套件。
    - [使用 SSMS 部署 SSIS 套件](./ssis-quickstart-deploy-ssms.md)
    - [使用 Transact-SQL 部署 SSIS 套件 (VS Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [從命令提示字元中部署 SSIS 套件](./ssis-quickstart-deploy-cmdline.md)
    - [使用 PowerShell 部署 SSIS 套件](ssis-quickstart-deploy-powershell.md)
    - [使用 C# 部署 SSIS 套件](./ssis-quickstart-deploy-dotnet.md) 
- 執行已部署的套件。 若要執行套件，您可以從數個工具和語言進行選擇。 如需詳細資訊，請參閱下列文章：
    - [使用 SSMS 執行 SSIS 套件](./ssis-quickstart-run-ssms.md)
    - [使用 Transact-SQL 執行 SSIS 套件 (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [使用 Transact-SQL 執行 SSIS 套件 (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [從命令提示字元中執行 SSIS 套件](./ssis-quickstart-run-cmdline.md)
    - [使用 PowerShell 執行 SSIS 套件](ssis-quickstart-run-powershell.md)
    - [使用 C# 執行 SSIS 套件](./ssis-quickstart-run-dotnet.md) 
