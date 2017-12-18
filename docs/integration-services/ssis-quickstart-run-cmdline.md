---
title: "從命令提示字元中執行 SSIS 套件 | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2c2b83605714e01961c50d71e83ba57691bc3833
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>從命令提示字元使用 DTExec.exe 執行 SSIS 套件
本快速入門教學課程會示範如何以適當的參數執行 `DTExec.exe`，從命令提示字元執行 SSIS 套件。

> [!NOTE]
> 本文中描述的方法尚未以部署到 Azure SQL Database 伺服器的套件測試。

如需 `DTExec.exe` 的詳細資訊，請參閱 [dtexec 公用程式](https://docs.microsoft.com/en-us/sql/integration-services/packages/dtexec-utility)。

## <a name="run-a-package-with-dtexec"></a>使用 dtexec 執行套件

如果包含 `DTExec.exe` 的資料夾不在 `path` 環境變數中，您可能需要使用 `cd` 命令以切換到其目錄。 若是 SQL Server 2017，此資料夾通常位於 `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`。

使用下例中所用的參數值，程式會執行位在指定的 SSIS 伺服器資料夾路徑中的套件，此伺服器就是裝載 SSIS 目錄資料庫 (SSISDB) 的伺服器。 `/Server` 參數會提供伺服器名稱。 程式會以目前具有 Windows 整合式驗證的使用者身分連線。 若要使用 SQL 驗證，請指定有適當值的 `/User` 和 `Password` 參數。

1. 開啟 [命令提示字元] 視窗。

2. 執行 `DTExec.exe` 並至少提供 `ISServer` 和 `Server` 參數的值，如下列範例所示：

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>後續的步驟
- 請考慮使用其他方式來執行套件。
    - [使用 SSMS 執行 SSIS 套件](./ssis-quickstart-run-ssms.md)
    - [使用 Transact-SQL 執行 SSIS 套件 (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [使用 Transact-SQL 執行 SSIS 套件 (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [使用 PowerShell 執行 SSIS 套件](ssis-quickstart-run-powershell.md)
    - [使用 C# 執行 SSIS 套件](./ssis-quickstart-run-dotnet.md) 
