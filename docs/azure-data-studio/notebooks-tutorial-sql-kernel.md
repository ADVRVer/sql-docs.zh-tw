---
title: Azure Data Studio 中的 SQL 核心筆記本
description: 本教學課程說明如何建立和執行 SQL Server 筆記本。
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray, alayu
ms.topic: tutorial
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 80b44b0cd69a3982be87e1fd0d000a6d6393a7c7
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531491"
---
# <a name="create-and-run-a-sql-server-notebook"></a>建立並執行 SQL Server 筆記本

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

本教學課程示範如何使用 SQL Server 在 Azure Data Studio 中建立及執行筆記本。

## <a name="prerequisites"></a>Prerequisites

- [已安裝 Azure Data Studio](download-azure-data-studio.md)
- 已安裝 SQL Server
  - [Windows](../database-engine/install-windows/install-sql-server.md)
  - [Linux](../linux/sql-server-linux-setup.md)

## <a name="new-notebook"></a>新增筆記本

下列步驟說明如何在 Azure Data Studio 中建立筆記本檔案：

1. 在 Azure Data Studio 中，連線到 SQL Server。

2. 在 [伺服器]  視窗中，於 [連線]  下方選取。 然後選取 [新增筆記本]  。

   ![開啟筆記本](media/notebook-tutorial/azure-data-studio-open-notebook.png)

3. 等候 [核心]  和目標內容 ([附加至]  ) 填入。 確認 [核心]  已設定為 [SQL]  ，並為 SQL Server 設定 [附加至]  (在此案例為 *localhost*)。

   ![設定 [核心] 和 [附加至]](media/notebook-tutorial/set-kernel-and-attach-to.png)

## <a name="run-a-notebook-cell"></a>執行筆記本資料格

您可以按下資料格左側的播放按鈕，執行每個筆記本資料格。 資料格完成執行之後，會在筆記本中顯示結果。

### <a name="code"></a>程式碼

選取工具列中的 [+程式碼]  命令來新增程式碼儲存格。

![筆記本工具列](media/notebooks-guidance/notebook-toolbar.png)

此範例會建立新的資料庫。

```sql
USE master
GO

   -- Drop the database if it already exists
IF  EXISTS (
        SELECT name
        FROM sys.databases
        WHERE name = N'TestNotebookDB'
   )
DROP DATABASE TestNotebookDB
GO

-- Create the database
CREATE DATABASE TestNotebookDB
GO
```

   ![執行筆記本資料格](media/notebook-tutorial/run-notebook-cell.png)

如果您執行會傳回結果的指令碼，則可將該結果儲存為不同的格式。

- 另存為 CSV
- 另存為 Excel
- 另存為 JSON
- 另存為 XML

在此案例中，我們會使用 [PI](../t-sql/functions/pi-transact-sql.md) 的傳回結果。

```sql
SELECT PI() AS PI;
GO
```

![執行筆記本資料格](media/notebook-tutorial/run-notebook-cell-2.png)

### <a name="text"></a>Text

選取工具列中的 [+文字]  命令來新增文字儲存格。

![筆記本工具列](media/notebooks-guidance/notebook-toolbar.png)

資料格會變更為編輯模式；現在當您鍵入 Markdown 時，即可同時查看預覽

![Markdown 儲存格](media/notebooks-guidance/notebook-markdown-cell.png)

選取文字儲存格以外的地方會顯示 Markdown 文字。

![Markdown 文字](media/notebooks-guidance/notebook-markdown-preview.png)

## <a name="next-steps"></a>後續步驟

深入了解筆記本：

- [如何搭配 SQL Server 使用筆記本](notebooks-guidance.md)

- [如何管理 Azure Data Studio 中的 Notebook](notebooks-manage-sql-server.md)

- [執行使用 Spark 的範例筆記本](../big-data-cluster/notebooks-tutorial-spark.md)