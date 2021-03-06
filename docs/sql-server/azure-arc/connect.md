---
title: 連線至 Azure Arc
titleSuffix: ''
description: 將 SQL Server 執行個體連線到 Azure Arc
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: e80892bfef7ee2c8cf22aef1b491ab5ea0c0addd
ms.sourcegitcommit: 442fbe1655d629ecef273b02fae1beb2455a762e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93235562"
---
# <a name="connect-your-sql-server-to-azure-arc"></a>將 SQL Server 連線到 Azure Arc

您可以遵循下列步驟，將內部部署 SQL Server 執行個體連線到 Azure Arc。

## <a name="prerequisites"></a>必要條件

* 您的電腦至少已安裝一個 SQL Server 執行個體
* 針對 Windows 電腦，您已安裝 Azure PowerShell。 依照指示來[安裝 Azure PowerShell](/powershell/azure/install-az-ps)。
* 針對 Linux 電腦，您已下載 Azure CLI 並連線您的 Azure 帳戶。 依照指示來[安裝 Azure CLI](/cli/azure/install-azure-cli-apt)。
* 已註冊 **Microsoft.AzureData** 資源提供者。 如需資源提供者的詳細資訊，請參閱＜Azure 資源提供者和類型＞。
    * 在 PowerShell 上，執行 `Register-AzResourceProvider -ProviderNamespace Microsoft.AzureData`
    * 在 Linux 上，執行 `az provider register --namespace 'Microsoft.AzureData`



## <a name="generate-a-registration-script-for-sql-server"></a>產生 SQL Server 的註冊指令碼

在此步驟中，您會產生指令碼來探索電腦上安裝的所有 SQL Server 執行個體，並將其註冊為 [SQL Server - Azure Arc] 資源。 如果未向 Azure Arc 註冊主控實體或虛擬機器，則指令碼會自動執行此作業。

1. 搜尋 [SQL Server - Azure Arc] 資源類型，並透過建立刀鋒視窗新增一個。

![開始建立](media/join/start-creation-of-sql-server-azure-arc-resource.png)
    
2. 檢閱必要條件並移至 [伺服器詳細資料] 索引標籤。  

3. 選取訂用帳戶、資源群組、Azure 區域和主機作業系統。 如有需要，也可指定您的網路用來連線到網際網路的 Proxy。

> [!IMPORTANT]
> 如果裝載 SQL Server 執行個體的電腦已經[連線到 Azure Arc](/azure/azure-arc/servers/onboard-portal)，請務必選取包含對應 [電腦 - Azure Arc] 資源的相同資源群組。

![伺服器詳細資料](media/join/server-details-sql-server-azure-arc.png)

4. 移至 [執行指令碼] 索引標籤，並下載顯示的註冊指令碼。 入口網站會為您指定的主控 OS 產生指令碼。

![下載指令碼](media/join/download-script-sql-server-azure-arc.png)

## <a name="connect-the-installed-sql-server-instances-to-azure-arc"></a>大規模地將已安裝的 SQL Server 執行個體連線到 Azure Arc

在此步驟中，您將會採用從 Azure 入口網站下載的指令碼，並在目標實體或虛擬機器上予以執行。 因此，電腦上安裝的每個 SQL Server 執行個體將會註冊為 [SQL Server - Azure Arc] 資源。 此外，如果電腦本身未安裝來賓設定代理程式，則會自動安裝並註冊為 [電腦 - Azure Arc] 資源。

> [!NOTE]
> 請務必使用符合[必要條件](overview.md#prerequisites)中所述最低權限需求的帳戶來執行指令碼。

### <a name="windows"></a>Windows

1. 啟動 __powershell.exe__ 的系統管理執行個體，並使用您的 Azure 認證登入您的 PowerShell 模組。 遵循[登入指示](/powershell/azure/install-az-ps#sign-in)。

2. 執行下載的指令碼

   ```powershell
   & '.\RegisterSqlServerArc.ps1'
   ```

   > [!NOTE]
   > 如果您先前尚未安裝適用於 powershell 的 AZ 模組，則可能第一次看到遇到問題。 在此情況下，請遵循指令碼中的指示來安裝並連線您的帳戶，然後再次執行指令碼。

### <a name="linux"></a>Linux

1. 使用 Azure CLI 以您的 Azure 認證登入。 遵循[登入指示](/cli/azure/authenticate-azure-cli)

2. 將執行權限授予下載的指令碼並加以執行。

   ```bash
   sudo chmod +x ./RegisterSqlServerArc.sh
   ./RegisterSqlServerArc.sh
   ```

## <a name="register-sql-server-instances-on-multiple-machines"></a>在多部電腦上註冊 SQL Server 執行個體

您可以使用針對單一電腦產生的相同指令碼，將安裝在多部 Windows 或 Linux 電腦上的多個 SQL Server 執行個體連線到 Azure Arc。 遵循如何[大規模地將 SQL Server 執行個體連線到 Azure Arc](connect-at-scale.md) 的指示。

## <a name="validate-the-sql-server---azure-arc-resources"></a>驗證 SQL Server - Azure Arc 資源

移至 [Azure 入口網站](https://ms.portal.azure.com/#home)並開啟新註冊的 [SQL Server - Azure Arc] 資源進行驗證。

![驗證已連線的 SQL Server ](media/join/validate-sql-server-azure-arc.png)

## <a name="un-register-the-sql-server---azure-arc-resources"></a>取消註冊 SQL Server - Azure Arc 資源

若要移除現有的 [SQL Server - Azure Arc] 資源，請移至包含該資源的資源群組，並從群組中的資源清單將其移除。

![取消註冊 SQL Server](media/join/delete-sql-server-azure-arc.png)

## <a name="next-steps"></a>下一步

* [設定 SQL Server 執行個體的進階資料安全性](configure-advanced-data-security.md)

* [設定 SQL Server 執行個體的隨選 SQL 評量](assess.md)