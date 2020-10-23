---
title: 離線部署
titleSuffix: SQL Server big data clusters
description: 了解如何執行 SQL Server 2019 巨量資料叢集的離線部署，以及如何將容器映像載入私人存放庫。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0437880dbcf3bef50184daa9e52f8eba2a7e31b4
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257178"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>執行 SQL Server 巨量資料叢集的離線部署

本文描述如何執行 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] 的離線部署。 巨量資料叢集必須能夠存取 Docker 存放庫以從中提取容器映像。 離線安裝是將所需映像放入私人 Docker 存放庫的一種安裝方式。 該私人存放庫接著會用作新部署的映像來源。

## <a name="prerequisites"></a>Prerequisites

- 在任何支援的 Linux 發行版本或適用於 Mac/Windows 上的 Docker 安裝 Docker 引擎 1.8 以上版本。 如需詳細資訊，請參閱[安裝 Docker](https://docs.docker.com/engine/installation/)。

## <a name="load-images-into-a-private-repository"></a>將映像載入私人存放庫

下列步驟描述如何從 Microsoft 存放庫提取巨量資料叢集容器映像，然後將其推送至您的私人存放庫。

> [!TIP]
> 下列步驟說明此程序。 不過，若要簡化工作，您可以使用[自動化的指令碼](#automated)來取代以手動執行這些命令。

1. 重複下列命令以提取巨量資料叢集容器映像。 將 `<SOURCE_IMAGE_NAME>` 取代為每個[映像名稱](#images)。 將 `<SOURCE_DOCKER_TAG>` 取代為巨量資料叢集版本的標籤，例如 **2019-GDR1-ubuntu-16.04**。  

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. 登入目標私人 Docker 登錄。

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. 使用下列命令，為每個映像標記本機映像：

   ```PowerShell
   docker tag mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. 將本機映像推送至私人 Docker 存放庫：

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```
 
> [!WARNING]
> 當將巨量資料叢集映像推送至私人存放庫之後，請勿修改這些映像。 使用修改過映像來執行部署將導致不支援的巨量資料叢集設定。


### <a name="big-data-cluster-container-images"></a><a id="images"></a> 巨量資料叢集容器映像

離線安裝需要下列巨量資料叢集容器映像：
- **mssql-app-service-proxy**
- **mssql-control-watchdog**
- **mssql-controller**
- **mssql-dns**
- **mssql-hadoop**
- **mssql-mleap-serving-runtime**
- **mssql-mlserver-py-runtime**
- **mssql-mlserver-r-runtime**
- **mssql-monitor-collectd**
- **mssql-monitor-elasticsearch**
- **mssql-monitor-fluentbit**
- **mssql-monitor-grafana**
- **mssql-monitor-influxdb**
- **mssql-monitor-kibana**
- **mssql-monitor-telegraf**
- **mssql-security-knox**
- **mssql-security-support**
- **mssql-server-controller**
- **mssql-server-data**
- **mssql-ha-operator**
- **mssql-ha-supervisor**
- **mssql-service-proxy**
- **mssql-ssis-app-runtime**


## <a name="automated-script"></a><a id="automated"></a> 自動化指令碼

您可以使用自動化的 Python 指令碼來自動提取所有必要容器映像，並將其推送至私人存放庫。

> [!NOTE]
> Python 是使用指令碼的必要條件。 如需如何安裝 Python 的詳細資訊，請參閱 [Python 文件](https://wiki.python.org/moin/BeginnersGuide/Download)。

1. 從 Bash 或 PowerShell 下載包含 **Curl** 的指令碼：

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. 然後，使用下列其中一項命令來執行指令碼：

   **Windows：**

   ```PowerShell
   python push-bdc-images-to-custom-private-repo.py
   ```

   **Linux：**

   ```bash
   sudo python push-bdc-images-to-custom-private-repo.py
   ```

1. 遵循提示輸入 Microsoft 存放庫和您的私人存放庫資訊。 指令碼完成之後，所有必要映像都應該位於您的私人存放庫中。

1. 請遵循[這裡](deployment-custom-configuration.md#docker)的指示，以了解如何自訂 `control.json` 部署設定檔來使用您的容器登錄和存放庫。 請注意，您必須在部署前設定 `DOCKER_USERNAME` 和 `DOCKER_PASSWORD` 環境變數，以允許存取您的私人存放庫。

## <a name="install-tools-offline"></a>離線安裝工具

巨量資料叢集部署需要幾項工具，包括 **Python**、[!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)] 和 **kubectl**。 遵循下列步驟，在離線伺服器上安裝這些工具。

### <a name="install-python-offline"></a><a id="python"></a> 離線安裝 python

1. 在能存取網際網路的電腦上，下載下列其中一個包含 Python 的壓縮檔案：

   | 作業系統 | 下載 |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. 將壓縮檔案複製到目標機器，並將其解壓縮至您選擇的資料夾。

1. (僅適用於 Windows) 在該資料夾中執行 `installLocalPythonPackages.bat`，並將相同資料夾的完整路徑傳遞為參數。

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

### <a name="install-azdata-offline"></a><a id="azdata"></a> 離線安裝 azdata

1. 在能存取網際網路並具有 [Python](https://wiki.python.org/moin/BeginnersGuide/Download) 的電腦上執行下列命令，將所有 [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)] 套件下載至目前的資料夾。

   ```PowerShell
   pip download -r https://aka.ms/azdata
   ```

1. 將下載的套件和 `requirements.txt` 檔案複製到目標電腦。

1. 在目標電腦上執行下列命令，並指定您將先前檔案複製到其中的資料夾。

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a name="install-kubectl-offline"></a><a id="kubectl"></a> 離線安裝 kubectl

若要將 **kubectl** 安裝至離線電腦，請遵循下列步驟。

1. 使用 **Curl** 將 **kubectl** 下載至您選擇的資料夾。 如需詳細資訊，請參閱[使用 Curl 安裝 kubectl 二進位](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl)。

1. 將資料夾複製到目標電腦。

## <a name="deploy-from-private-repository"></a>從私人存放庫部署

若要從私人存放庫部署，請使用[部署指南](deployment-guidance.md)中所述的步驟，但使用可指定您私人 Docker 存放庫資訊的自訂部署設定檔。 下列 [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)] 命令示範如何在名為 `control.json` 的自訂部署設定檔中變更 Docker 設定：

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.repository=<your-docker-repository>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.registry=<your-docker-registry>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.imageTag=<your-docker-image-tag>"
```

部署會提示您提供 Docker 使用者名稱和密碼，或您也可以在 `DOCKER_USERNAME` 和 `DOCKER_PASSWORD` 環境變數中指定。

## <a name="next-steps"></a>後續步驟

如需巨量資料叢集部署的詳細資訊，請參閱[如何在 Kubernetes 上部署 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](deployment-guidance.md)。
