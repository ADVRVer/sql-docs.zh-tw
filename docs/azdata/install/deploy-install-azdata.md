---
title: 安裝 Azure Data CLI (azdata)
titleSuffix: ''
description: 了解如何安裝 Azure Data CLI (azdata) 工具。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 82aa3a2795328804a10a76e9ecd8af80f3bf7152
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257393"
---
# <a name="install-azure-data-cli-azdata"></a>安裝 [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

[!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] 是以 Python 撰寫的命令列公用程式，可透過 REST API 啟動及管理資料服務。 

## <a name="find-latest-version"></a>尋找最新版本

您一律可以在 [https://aka.ms/azdata](https://aka.ms/azdata) 找到最新版本的檔案清單。

若要找出已安裝的版本，並查看是否需要更新，請執行 `azdata --version`。

## <a name="os-specific-instructions"></a>OS 特定指示

* [在 Windows 上安裝](../install/deploy-install-azdata-installer.md)
* [在 macOS 上安裝](../install/deploy-install-azdata-macos.md)
* 在 Linux 或[適用於 Linux 的 Windows 子系統 (WSL)](/windows/wsl/about/) 上安裝
   * [在 Debian 或 Ubuntu 上使用 apt 安裝](../install/deploy-install-azdata-linux-package.md)
   * [在 RHEL 或 CentOS 上使用 yum 安裝](../install/deploy-install-azdata-yum.md)
   * [在 openSUSE 或 SLE 上使用 Zypper 安裝](../install/deploy-install-azdata-zypper.md)
   * [從指令碼安裝](../install/deploy-install-azdata-pip.md)

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="next-steps"></a>後續步驟

使用 azdata 搭配巨量資料叢集，請參閱[什麼是 [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]？](../../big-data-cluster/big-data-cluster-overview.md)。

使用 azdata 搭配[已啟用 Azure Arc 的資料服務](/azure/azure-arc/data/)
