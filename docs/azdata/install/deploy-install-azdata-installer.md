---
title: 使用 Windows Installer 安裝 azdata
titleSuffix: ''
description: 了解如何使用安裝程式來安裝 azdata 工具。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a33e43386c44ec2ab60166ef57a502fc592c8d73
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914953"
---
# <a name="install-azdata-to-manage-big-data-clusters-2019-with-windows-installer"></a>使用 Windows Installer 來安裝 `azdata` 以管理 [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/azdata.md)]

本文描述如何在 Windows 上安裝 `azdata`。 在安裝 Windows 之前，`azdata` 的安裝需要 `pip`。

>針對 Linux (Ubuntu)，請參閱[使用安裝程式來安裝 `azdata`](./deploy-install-azdata-linux-package.md)。

目前沒有任何套件管理員能夠在其他作業系統或發行版上安裝 `azdata`。 針對這些平台，請參閱[在沒有套件管理員的情況下安裝 `azdata`](./deploy-install-azdata.md)。

## <a name="install-azdata-with-the-microsoft-windows-installer"></a>使用 Microsoft Windows Installer 安裝 `azdata`

若要使用 Microsoft Windows Installer 安裝 `azdata`，

1. 如果 `pip` 是使用 `azdata` 來進行安裝，請將其移除。 如果 `azdata` 是使用 Windows Installer 來進行安裝，請繼續進行下一個步驟。
1. 使用 Windows Installer 來安裝 `azdata`。

### <a name="uninstall-if-previous-installation-done-with-pip"></a>如果先前使用 `pip` 來進行安裝，請解除安裝

如果您已安裝任何舊版的 `azdata`，請務必先解除安裝，然後安裝最新版本。

   若要移除 `azdata` 的發行候選版本，請執行下列命令。

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

移除之後，[在 Windows 上安裝 `azdata`](#install-azdata-windows)。

>[!NOTE]
>如果您先前的安裝是使用 MSI 完成，則在使用 MSI 安裝程式之前，您將不需要解除安裝任何目前版本。

### <a name="install-with-windows-installer"></a><a id="install-azdata-windows"></a>使用 Windows Installer 來進行安裝

使用 Windows Installer 在 Windows 上安裝或更新 `azdata`。

[下載 `azdata` Windows Installer](https://aka.ms/azdata-msi)。

當安裝程式詢問是否可以對電腦進行變更時，請按一下 `Yes`。

### <a name="uninstall-azdata-with-windows-installer"></a>使用 Windows Installer 來解除安裝 `azdata`

若要使用 Windows Installer 來解除安裝 `azdata`，請遵循適當作業系統的指示。

| 平台      | Instructions                                           |
| ------------- |--------------------------------------------------------|
| Windows 10| [開始] > [設定] > [應用程式]                                |
| Windows 8     | [啟動] > [控制台] -> [程式集] -> [解除安裝程式] |

要解除安裝的程式稱為 `Azdata CLI`。 選取此應用程式，然後按一下 `Uninstall` 按鈕。

## <a name="next-steps"></a>後續步驟

如需巨量資料叢集的詳細資訊，請參閱[什麼是 [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]？](../../big-data-cluster/big-data-cluster-overview.md)

使用 azdata 搭配[已啟用 Azure Arc 的資料服務](/azure/azure-arc/data/)
