---
title: 設定 Azure Kubernetes 服務
titleSuffix: SQL Server big data clusters
description: 了解如何設定適用於 SQL Server 2019 巨量資料叢集 （預覽） 部署的 Azure Kubernetes Service (AKS)。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 07/10/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 872988b29cddc202ea2c0f199548bc28b946b918
ms.sourcegitcommit: e366f702c49d184df15a9b93c2c6a610e88fa0fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826524"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-big-data-cluster-deployments"></a>設定適用於 SQL Server 的巨量資料叢集部署的 Azure Kubernetes 服務

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

本文說明如何設定適用於 SQL Server 2019 巨量資料叢集 （預覽） 部署的 Azure Kubernetes Service (AKS)。

AKS 可讓您更輕鬆地建立、 設定及管理預先設定的虛擬機器的叢集使用來執行容器化應用程式的 Kubernetes 叢集。 這可讓您使用現有技能，或運用大量且不斷成長的社群專業知識，來部署和管理 Microsoft Azure 上的容器型應用程式。

這篇文章說明部署 Kubernetes AKS 使用 Azure CLI 上的步驟。 如果您沒有 Azure 訂用帳戶，請在您開始前建立免費帳戶。

> [!TIP] 
> 部署 AKS 和 SQL Server 的巨量資料叢集的範例 python 指令碼，請參閱[快速入門：將巨量資料叢集的 Azure Kubernetes Service (AKS) 上的 SQL Server 部署](quickstart-big-data-cluster-deploy.md)。

## <a name="prerequisites"></a>必要條件

- [部署 SQL Server 2019 巨量資料的工具](deploy-big-data-tools.md):
   - **Kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019 延伸模組**
   - **Azure CLI**

- 最小值 1.10 Kubernetes 伺服器版本。 您必須使用 AKS，`--kubernetes-version`參數來指定預設值不同的版本。

- 以驗證在 AKS 上的基本案例時獲得最佳體驗，請使用：
   - 所有節點間的 8 個 Vcpu
   - 32 GB 的每個 VM 的記憶體
   - 在所有節點之間的 24 或更多連接磁碟

   > [!TIP]
   > Azure 基礎結構提供多個 Vm 的大小選項，請參閱 <<c0> [ 此處](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)針對您打算要部署的區域中選取項目。

## <a name="create-a-resource-group"></a>建立資源群組

Azure 資源群組是在哪一項 Azure 資源部署與管理的邏輯群組。 下列步驟登入 Azure，並建立 AKS 叢集的資源群組。

1. 在命令提示字元中，執行下列命令，並遵循提示來登入您的 Azure 訂用帳戶：

    ```azurecli
    az login
    ```

1. 如果您有多個訂用帳戶，您可以執行下列命令來檢視您所有的訂閱：

   ```azurecli
   az account list
   ```

1. 如果您想要將變更為不同的訂用帳戶，您可以執行此命令：

   ```azurecli
   az account set --subscription <subscription id>
   ```

1. 建立的資源群組**az 群組建立**命令。 下列範例會建立名為的資源群組`sqlbdcgroup`在`westus2`位置。

   ```azurecli
   az group create --name sqlbdcgroup --location westus2
   ```

## <a name="verify-available-kubernetes-versions"></a>確認可用的 Kubernetes 版本

使用 Kubernetes 的最新可用版本。 最新的可用版本取決於您要在其中部署叢集的位置。 下列命令會傳回在特定位置的可用 Kubernetes 版本。

執行命令之前，請更新指令碼。 取代`<Azure data center>`叢集中的位置。

   **bash**

   ```bash
   az aks get-versions \
   --location <Azure data center> \
   --query orchestrators \
   --o table
   ```

   **PowerShell**

   ```powershell
   az aks get-versions `
   --location <Azure data center> `
   --query orchestrators `
   --o table
   ```

選擇您的叢集的最新可用版本。 記錄的版本號碼。 您將在下一個步驟中使用它。

## <a name="create-a-kubernetes-cluster"></a>建立 Kubernetes 叢集

1. 在與 AKS 建立 Kubernetes 叢集[az aks 建立](https://docs.microsoft.com/cli/azure/aks)命令。 下列範例會建立名為 Kubernetes 叢集*kubcluster*使用一個 Linux 代理程式節點大小**Standard_L8s**。

   執行指令碼之前，請取代`<version number>`您在上一個步驟中識別的版本號碼。

   請確定您在先前各節中使用的相同資源群組中建立 AKS 叢集。

   **bash:**

   ```bash
   az aks create --name kubcluster \
   --resource-group sqlbdcgroup \
   --generate-ssh-keys \
   --node-vm-size Standard_L8s \
   --node-count 1 \
   --kubernetes-version <version number>
   ```

   **PowerShell:**

   ```powershell
   az aks create --name kubcluster `
   --resource-group sqlbdcgroup `
   --generate-ssh-keys `
   --node-vm-size Standard_L8s `
   --node-count 1 `
   --kubernetes-version <version number>
   ```

   您可以增加或減少的 Kubernetes 代理程式節點數目，藉由變更`--node-count <n>`其中`<n>`是您想要使用的代理程式節點數目。 這不包括 master 的 Kubernetes 節點，其在幕後受 AKS。 先前的範例只會使用針對評估用途的單一節點。

   幾分鐘之後，此命令會完成，並傳回 JSON 格式化叢集的相關資訊。

   > [!TIP]
   > 如果您收到 AKS 中建立叢集的任何錯誤，請參閱[疑難排解 區段](#troubleshoot)這篇文章。

1. 儲存 JSON 輸出以供稍後使用前一個命令。

## <a name="connect-to-the-cluster"></a>連線到叢集

1. 若要設定 kubectl 來連線到 Kubernetes 叢集，請執行[az aks get-credentials 來取得認證](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials)命令。 此步驟中下載憑證，並設定 kubectl CLI 來使用它們。

   ```azurecli
   az aks get-credentials --resource-group=sqlbdcgroup --name kubcluster
   ```

1. 若要驗證您的叢集連線，請使用[kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)命令來傳回叢集節點的清單。  下列範例顯示輸出時有 1 部主機，以及 3 個代理程式節點。

   ```bash
   kubectl get nodes
   ```

## <a id="troubleshoot"></a> 疑難排解

如果您有使用上述命令建立 Azure Kubernetes 服務的任何問題，請嘗試下列解決方法：

- 請確定您已安裝[最新的 Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)。
- 請嘗試相同步驟，使用不同的資源群組與叢集名稱。

## <a name="next-steps"></a>後續步驟

這篇文章中的步驟會設定在 AKS 中 Kubernetes 叢集。 下一個步驟是部署在 AKS 的 Kubernetes 叢集上的 SQL Server 2019 巨量資料叢集。 如需有關如何部署巨量資料叢集的詳細資訊，請參閱下列文章：

[如何部署 SQL Server 在 Kubernetes 上的巨量資料叢集](deployment-guidance.md)
