---
title: SQL Server dacpac 延伸模組
titleSuffix: Azure Data Studio
description: 安裝和使用適用於 Azure Data Studio 的 SQL Server dacpac 延伸模組 (預覽)
ms.custom: seodec18
ms.date: 10/21/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 769e6157e7d84702716dfce79d0217efeee83076
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783341"
---
# <a name="sql-server-dacpac-extension-preview"></a>SQL Server dacpac 延伸模組 (預覽)

[資料層應用程式精靈]  提供部署和解壓縮 .dacpac 檔案，以及匯入和匯出 .bacpac 檔案的易於使用體驗。

此體驗目前為初始預覽狀態。 請在[這裡](https://github.com/microsoft/azuredatastudio/issues)回報問題和功能要求。


## <a name="features"></a>功能

* 將 dacpac 部署至 SQL Server 執行個體
* 將 SQL Server 執行個體解壓縮至 dacpac
* 從 bacpac 建立資料庫
* 將結構描述和資料匯出至 bacpac

![dacpac 延伸模組示範 gif](media/extensions/sql-server-dacpac-extension/dacpac-extension-demo.gif)


## <a name="why-would-i-use-the-data-tier-application-wizard"></a>為什麼使用 [資料層應用程式精靈]？

精靈可讓管理 dacpac 和 bacpac 檔案更為容易，其可簡化開發及部署支援應用程式的資料層元素。 若要深入了解使用資料層應用程式，[請參閱我們的文件。](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)


## <a name="install-the-extension"></a>安裝延伸模組

1. 選取延伸模組圖示以檢視可用的延伸模組。

    ![延伸模組管理員圖示](media/extensions/extension-manager-icon.png)

2. 搜尋 **SQL Server dacpac** 延伸模組並加以選取，以檢視其詳細資料。 按一下 [安裝] 以新增延伸模組。

3. 安裝之後，請**重新載入**以在 Azure Data Studio 中啟用延伸模組 (只有在第一次安裝延伸模組時才需要)。


## <a name="launch-the-data-tier-application-wizard"></a>啟動資料層應用程式精靈

若要啟動精靈，請在 [物件總管] 中以滑鼠右鍵按一下資料庫資料夾，或以滑鼠右鍵按一下特定資料庫。 然後，請按一下 [資料層應用程式精靈]。

![dacpac 延伸模組啟動功能表](media/extensions/sql-server-dacpac-extension/dacpac-extension-launch.png)


## <a name="next-steps"></a>後續步驟

若要深入了解 dacpac，[請參閱我們的文件。](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)