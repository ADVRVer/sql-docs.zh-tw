---
title: azdata bdc 參考
titleSuffix: SQL Server big data clusters
description: azdata bdc 命令的參考文章。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 44b0f8daafec86714bb8161c1d30130eed3d480d
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653448"
---
# <a name="azdata-bdc"></a>azdata bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

下列文章提供 **azdata** 工具中 **bdc** 命令的參考。 如需其他 **azdata** 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)。

## <a name="commands"></a>命令

|     |     |
| --- | --- |
[azdata bdc create](#azdata-bdc-create) | 建立巨量資料叢集。
[azdata bdc delete](#azdata-bdc-delete) | 刪除巨量資料叢集。
[azdata bdc config](reference-azdata-bdc-config.md) | 組態命令。
[azdata bdc endpoint](reference-azdata-bdc-endpoint.md) | 端點命令。
[azdata bdc status](reference-azdata-bdc-status.md) | 狀態命令。
[azdata bdc debug](reference-azdata-bdc-debug.md) | 偵錯命令。
[azdata bdc control](reference-azdata-bdc-control.md) | 控制項命令。
[azdata bdc pool](reference-azdata-bdc-pool.md) | 集區命令。
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | HDFS 模組提供用來存取 HDFS 檔案系統的命令。
[azdata bdc spark](reference-azdata-bdc-spark.md) | Spark 命令可讓使用者透過建立和管理工作階段、陳述式和批次，與 Spark 系統進行互動。
## <a name="azdata-bdc-create"></a>azdata bdc create
建立 SQL Server 巨量資料叢集 - 系統上必須有 kube 設定，以及下列環境變數 ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD', 'MSSQL_SA_PASSWORD', 'KNOX_PASSWORD']。
```bash
azdata bdc create [--name -n] 
                  [--config-profile -c]  
                  [--accept-eula -a]  
                  [--node-label -l]  
                  [--force -f]
```
### <a name="examples"></a>範例

引導式 BDC 部署體驗；您將會接收到所需值的提示。

```bash
azdata bdc create
```

包含引數的 BDC 部署。

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test
```
設定檔中具有指定名稱 (而不是預設名稱) 的 BDC 部署。
```bash
azdata bdc create --name <cluster_name> --accept-eula yes --config-profile aks-dev-test --force
```

包含引數的 BDC 部署 - 使用 --force 旗標時，不會提供任何提示。

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test --force
```

### <a name="optional-parameters"></a>選擇性參數
#### `--name -n`
巨量資料叢集名稱，用於 kubernetes 命名空間。
#### `--config-profile -c`
巨量資料叢集組態設定檔，用於部署叢集：['aks-dev-test', 'kubeadm-dev-test', 'minikube-dev-test']
#### `--accept-eula -a`
您接受授權條款嗎? [yes/no]。 如果您不想要使用此引數，可以將環境變數 ACCEPT_EULA 設定為 'yes'。 此產品的授權條款可于[https://go.microsoft.com/fwlink/?LinkId=2002534](https://go.microsoft.com/fwlink/?LinkId=2002534)查看。
#### `--node-label -l`
巨量資料叢集節點標籤，用來指定要部署至的目標節點。
#### `--force -f`
強制建立，系統不會提示使用者輸入任何值，而且所有問題都會列印成標準錯誤輸出的一部分。
### <a name="global-arguments"></a>全域引數
#### `--debug`
增加記錄詳細資訊，以顯示所有偵錯記錄。
#### `--help -h`
顯示此說明訊息並結束。
#### `--output -o`
輸出格式。  允許的值：json、jsonc、table、tsv。  預設值：json。
#### `--query -q`
JMESPath 查詢字串。 如需詳細資訊和範例，請參閱 [http://jmespath.org/](http://jmespath.org/])。
#### `--verbose`
增加記錄詳細資訊。 使用 --debug 來取得完整偵錯記錄。
## <a name="azdata-bdc-delete"></a>azdata bdc delete
刪除 SQL Server 巨量資料叢集 - 系統上必須有 kube 設定，以及下列環境變數 ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD']。
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>範例
BDC 刪除，其中控制器使用者名稱和密碼已在您的系統環境中設定。
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>必要參數
#### `--name -n`
巨量資料叢集名稱，用於 kubernetes 命名空間。
### <a name="optional-parameters"></a>選擇性參數
#### `--force -f`
強制刪除巨量資料叢集。
### <a name="global-arguments"></a>全域引數
#### `--debug`
增加記錄詳細資訊，以顯示所有偵錯記錄。
#### `--help -h`
顯示此說明訊息並結束。
#### `--output -o`
輸出格式。  允許的值：json、jsonc、table、tsv。  預設值：json。
#### `--query -q`
JMESPath 查詢字串。 如需詳細資訊和範例，請參閱 [http://jmespath.org/](http://jmespath.org/])。
#### `--verbose`
增加記錄詳細資訊。 使用 --debug 來取得完整偵錯記錄。

## <a name="next-steps"></a>後續步驟

如需其他 **azdata** 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)。 如需有關如何安裝**azdata**工具的詳細資訊, 請參閱[install azdata to [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]manage ](deploy-install-azdata.md)。
