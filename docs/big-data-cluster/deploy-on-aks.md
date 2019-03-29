---
title: 設定 Azure Kubernetes 服務
titleSuffix: SQL Server 2019 big data clusters
description: 了解如何設定適用於 SQL Server 2019 巨量資料叢集 （預覽） 部署的 Azure Kubernetes Service (AKS)。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: ac8632c3966da750e9eb7d7053dad1d102760c8c
ms.sourcegitcommit: 0c049c539ae86264617672936b31d89456d63bb0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58618235"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-big-data-cluster-preview-deployments"></a>設定適用於 SQL Server 2019 巨量資料叢集 （預覽） 部署的 Azure Kubernetes 服務

本文說明如何設定適用於 SQL Server 2019 巨量資料叢集 （預覽） 部署的 Azure Kubernetes Service (AKS)。

AKS 可讓您更輕鬆地建立、 設定及管理預先設定的虛擬機器的叢集使用來執行容器化應用程式的 Kubernetes 叢集。 這可讓您使用現有技能，或運用大量且不斷成長的社群專業知識，來部署和管理 Microsoft Azure 上的容器型應用程式。

這篇文章說明部署 Kubernetes AKS 使用 Azure CLI 上的步驟。 如果您沒有 Azure 訂用帳戶，請在您開始前建立免費帳戶。

> [!TIP] 
> 部署 AKS 和 SQL Server 的巨量資料叢集的範例 python 指令碼，請參閱[快速入門：將巨量資料叢集的 Azure Kubernetes Service (AKS) 上的 SQL Server 部署](quickstart-big-data-cluster-deploy.md)。

## <a name="prerequisites"></a>先決條件

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

1. 建立的資源群組**az 群組建立**命令。 下列範例會建立名為的資源群組`sqlbigdatagroup`在`westus2`位置。

   ```azurecli
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>建立 Kubernetes 叢集

1. 在與 AKS 建立 Kubernetes 叢集[az aks 建立](https://docs.microsoft.com/cli/azure/aks)命令。 下列範例會建立名為 Kubernetes 叢集*kubcluster*使用一個 Linux 代理程式節點大小**Standard_L8s**。 請確定您在先前各節中使用的相同資源群組中建立 AKS 叢集。

    ```azurecli
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_L8s \
    --node-count 1 \
    --kubernetes-version 1.10.9
    ```

   您可以增加或減少的 Kubernetes 代理程式節點數目，藉由變更`--node-count <n>`其中`<n>`是您想要使用的代理程式節點數目。 這不包括 master 的 Kubernetes 節點，其在幕後受 AKS。 先前的範例只會使用針對評估用途的單一節點。

   幾分鐘之後，此命令會完成，並傳回 JSON 格式化叢集的相關資訊。

1. 儲存 JSON 輸出以供稍後使用前一個命令。

## <a name="connect-to-the-cluster"></a>連線到叢集

1. 若要設定 kubectl 來連線到 Kubernetes 叢集，請執行[az aks get-credentials 來取得認證](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials)命令。 此步驟中下載憑證，並設定 kubectl CLI 來使用它們。

   ```azurecli
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. 若要驗證您的叢集連線，請使用[kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)命令來傳回叢集節點的清單。  下列範例顯示輸出時有 1 部主機，以及 3 個代理程式節點。

   ```
   kubectl get nodes
   ```

## <a name="next-steps"></a>後續步驟

這篇文章中的步驟會設定在 AKS 中 Kubernetes 叢集。 下一個步驟是將 SQL Server 2019 巨量資料部署到叢集。 如需有關如何部署巨量資料叢集的詳細資訊，請參閱下列文章：

[如何部署 SQL Server 在 Kubernetes 上的巨量資料叢集](deployment-guidance.md)
