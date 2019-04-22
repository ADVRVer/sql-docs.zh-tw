---
title: 版本資訊
titleSuffix: SQL Server big data clusters
description: 本文說明 SQL Server 2019 巨量資料叢集 （預覽） 的已知的問題與最新的更新。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/28/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 3c999d82df4e8b73e290456ad5d3601712747ef9
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860522"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>版本資訊適用於 SQL Server 上的巨量資料叢集

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

本文章列出的更新，並了解最新版本的 SQL Server 的巨量資料叢集的問題。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp24"></a> CTP 2.4 （年 3 月）

下列各節說明的新功能與 SQL Server 2019 CTP 2.4 中的巨量資料叢集的已知的問題。

### <a name="whats-new"></a>新功能

| 新功能或更新 | 詳細資料 |
|:---|:---|
| 說明在 Spark 中透過 TensorFlow 執行深度學習時的 GPU 支援。 | [部署具有 GPU 支援的巨量資料叢集並執行 TensorFlow](spark-gpu-tensorflow.md)。 |
| **SqlDataPool**並**SqlStoragePool**預設不會再建立資料來源。 | 視需要手動建立這些。 請參閱[已知問題](#externaltablesctp24)。 |
| 資料集區的 `INSERT INTO SELECT` 支援。 | 如需範例，請參閱[教學課程：將資料內嵌到 SQL Server 資料集區使用 TRANSACT-SQL](tutorial-data-pool-ingest-sql.md)。 |
| `FORCE SCALEOUTEXECUTION` 和`DISABLE SCALEOUTEXECUTION`選項。 | 強制或停用外部資料表上的查詢集區的計算使用。 例如， `SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)` 。 |
| 已更新的 AKS 部署建議。 | 在 AKS 上的巨量資料叢集時，我們現在建議使用單一節點的大小**Standard_L8s**。 |
| 將 Spark 執行階段升級至 Spark 2.4。 | |

### <a name="known-issues"></a>已知問題

下列各節說明此版本中的限制與已知的問題。

#### <a name="deployment"></a>部署

- 不支援從舊版升級的巨量資料的資料叢集。

   > [!IMPORTANT]
   > 您必須備份您的資料，然後再刪除現有的巨量資料叢集 (使用舊版**mssqlctl**) 才能部署最新版本。 如需詳細資訊，請參閱 <<c0> [ 升級到新版](deployment-guidance.md#upgrade)。

- 在部署之後在 AKS 上，您可能會看到部署的下列兩個警告事件。 這兩個事件的已知問題，但它們不會防止您成功部署在 AKS 上的巨量資料叢集。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- 如果巨量資料叢集部署失敗，不會移除相關聯的命名空間。 這可能會導致失去關聯的命名空間，在叢集上。 因應措施是手動刪除命名空間，才能部署具有相同名稱的叢集。

#### <a name="kubeadm-deployments"></a>kubeadm 部署

如果您要部署多部電腦上的 Kubernetes 使用 kubeadm，叢集系統管理入口網站不會正確顯示連線至巨量資料叢集所需的端點。 如果您遇到這個問題，使用下列因應措施若要探索的服務端點 IP 位址：

- 如果您從連接在叢集內，查詢服務 IP 端點，您想要連線到 Kubernetes。 例如，下列**kubectl**命令會顯示 SQL Server 的主要執行個體的 IP 位址：

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- 如果您從外部連線的叢集，請使用下列步驟來連接：

   1. 取得執行 SQL Server 的主要執行個體的節點的 IP 位址： `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`。

   1. 連接到 SQL Server 使用此 IP 位址的主要執行個體。

   1. 查詢**cluster_endpoint_table**其他外部端點的 master 資料庫中。

      如果失敗連接逾時，就可以在對應的節點進行防火牆處理。 在此情況下，您必須連絡您的 Kubernetes 叢集系統管理員，並要求為對外公開的節點 IP。 這可能是任何節點。 您接著可以使用該 IP 和對應的連接埠連接到叢集中執行的各種服務。 比方說，系統管理員可以執行以尋找此 IP:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>刪除叢集失敗

當您嘗試刪除與叢集**mssqlctl**，它就會失敗，發生下列錯誤：

```
2019-03-26 20:38:11.0614 UTC | INFO | Deleting cluster ...
Error processing command: "TypeError"
delete_namespaced_service() takes 3 positional arguments but 4 were given
Makefile:61: recipe for target 'delete-cluster' failed
make[2]: *** [delete-cluster] Error 1
Makefile:223: recipe for target 'deploy-clean' failed
make[1]: *** [deploy-clean] Error 2
Makefile:203: recipe for target 'deploy-clean' failed
make: *** [deploy-clean] Error 2
```

新的 Python Kubernetes 用戶端 （9.0.0 版） 已變更的刪除命名空間 API，這目前會中斷**mssqlctl**。 如果您已安裝較新 Kubernetes python 用戶端，這只會發生。 您可以藉由直接刪除叢集使用解決這個問題**kubectl** (`kubectl delete ns <ClusterName>`)，或者您可以安裝較舊的版本使用`sudo pip install kubernetes==8.0.1`。

#### <a id="externaltablesctp24"></a> 外部資料表

- 巨量資料叢集部署不會再建立**SqlDataPool**並**SqlStoragePool**外部資料來源。 您可以建立這些資料來源，以手動方式來支援資料虛擬化資料集區和儲存體集區。

   ```sql
   -- Create the SqlDataPool data source:
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');

   -- Create the SqlStoragePool data source:
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
   BEGIN
     IF SERVERPROPERTY('ProductLevel') = 'CTP2.3'
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-mssql-controller:8080');
     ELSE IF SERVERPROPERTY('ProductLevel') = 'CTP2.4'
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   END
   ```

- 可以建立具有不支援的資料行類型為資料表的資料集區外部資料表。 如果您查詢外部資料表時，您收到訊息如下所示：

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 如果您查詢儲存體集區外部資料表時，您可能會發生錯誤，如果在相同的時間基礎檔案複製到 HDFS。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 如果您要建立外部資料表以使用字元資料類型的 Oracle，Azure Data Studio virtualization 精靈會解譯為 VARCHAR 這些資料行中的外部資料表定義。 這會導致外部資料表 DDL 失敗。 請修改使用 NVARCHAR2 類型，或以手動方式建立 EXTERNAL TABLE 陳述式，而不是使用此精靈指定 NVARCHAR 的 Oracle 結構描述。

#### <a name="application-deployment"></a>應用程式部署

- 在呼叫 R、 Python 或 MLeap 應用程式從支援的 RESTful API 時，呼叫會逾時在 5 分鐘內。

#### <a name="spark-and-notebooks"></a>Spark 和 notebook

- POD IP 位址可能變更 Kubernetes 環境中，Pod 重新啟動時。 在案例中，重新啟動主要 pod，Spark 工作階段可能會失敗並`NoRoteToHostException`。 這因為不使用新的 IP 取得重新整理的 JVM 快取的位址。

- 如果您在 Windows 上有已安裝的 Jupyter 和個別的 Python，可能會失敗 Spark notebook。 若要解決此問題，請升級為最新版本的 Jupyter。

- 在筆記本中，如果您按一下**新增文字**命令時，文字資料格會新增 [預覽] 模式，而不是編輯模式。 您可以按一下 [預覽] 圖示，切換至編輯模式和編輯儲存格。

#### <a name="hdfs"></a>HDFS

- 如果您以滑鼠右鍵按一下檔案，以進行預覽，HDFS 中，您可能會看到下列錯誤：

   `Error previewing file: File exceeds max size of 30MB`

   目前沒有任何方法可預覽檔案大於 30 MB 的 Azure Data Studio。

- 不支援對 hdfs-site.xml 變更的 HDFS 組態變更。

#### <a name="security"></a>安全性

- SA_PASSWORD 屬於環境的且可探索 （例如在線傾印檔案）。 您必須在部署之後，重設 SA_PASSWORD 主要執行個體上。 這不是 bug，但安全性步驟。 如需有關如何變更 SA_PASSWORD 的 Linux 容器的詳細資訊，請參閱[變更 SA 密碼](../linux/quickstart-install-connect-docker.md#sapassword)。

- AKS 記錄檔可能包含適用於巨量資料叢集部署的 SA 密碼。

## <a id="ctp23"></a> CTP 2.3 （二月）

下列各節說明的新功能與 SQL Server 2019 CTP 2.3 中的巨量資料叢集的已知的問題。

### <a name="whats-new"></a>新功能

| 新功能或更新 | 詳細資料 |
| :---------- | :------ |
| 將在 IntelliJ 中的巨量資料叢集上的 Spark 作業提交。 | [將 SQL Server 在 IntelliJ 中的巨量資料叢集上的 Spark 作業提交](spark-submit-job-intellij-tool-plugin.md) |
| 適用於應用程式部署和叢集管理的常見 CLI。 | [如何部署 SQL Server 2019 巨量資料叢集 （預覽） 上的應用程式](big-data-cluster-create-apps.md) |
| VS Code 延伸模組，巨量資料叢集來部署應用程式。 | [如何使用 VS Code 來部署應用程式到 SQL Server 的巨量資料叢集](app-deployment-extension.md) |
| 若要變更**mssqlctl**工具命令使用方式。 | 如需詳細資訊，請參閱[mssqlctl 的已知問題](#mssqlctlctp23)。 |
| Sparklyr 用於巨量資料叢集 | [在 SQL Server 2019 巨量資料叢集中使用 Sparklyr](sparklyr-from-RStudio.md) |
| 將外部 HDFS 相容儲存體裝載至具備 **HDFS 階層處理**的巨量資料叢集。 | 請參閱[HDFS 分層](hdfs-tiering.md)。 |
| SQL Server 的主要執行個體與 HDFS/Spark 閘道的新統一的連線體驗。 | 請參閱[SQL Server 的主要執行個體和 HDFS/Spark 閘道](connect-to-big-data-cluster.md)。 |
| 刪除與叢集**mssqlctl 叢集刪除**現在會刪除只物件命名空間中的巨量資料叢集的一部分。 | 命名空間不會刪除。 不過，在舊版中此命令並未刪除整個命名空間。 |
| _安全性_端點名稱已變更和彙總。 | **服務-安全性-lb**並**服務-安全性-nodeport**已合併到**端點安全性**端點。 |
| _Proxy_端點名稱已變更和彙總。 | **服務-proxy-lb**並**服務-proxy-nodeport**已合併到**端點服務 proxy**端點。 |
| _控制器_端點名稱已變更和彙總。 | **服務-mssql-控制站-lb**並**服務-mssql-控制站-nodeport**已合併到**端點控制器**端點。 |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>已知問題

下列各節說明此版本中的限制與已知的問題。

#### <a name="deployment"></a>部署

- 不支援從舊版升級的巨量資料的資料叢集。

   > [!IMPORTANT]
   > 您必須備份您的資料，然後再刪除現有的巨量資料叢集 (使用舊版**mssqlctl**) 才能部署最新版本。 如需詳細資訊，請參閱 <<c0> [ 升級到新版](deployment-guidance.md#upgrade)。

- **ACCEPT_EULA**環境變數必須是"yes"或 [是] 以接受使用者授權合約。 舊版允許"y"和"Y"，但是這些不會再接受，且會導致部署失敗。

- **CLUSTER_PLATFORM**環境變數沒有預設值在舊版本中所顯示的一樣。

- 在部署之後在 AKS 上，您可能會看到部署的下列兩個警告事件。 這兩個事件的已知問題，但它們不會防止您成功部署在 AKS 上的巨量資料叢集。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- 如果巨量資料叢集部署失敗，不會移除相關聯的命名空間。 這可能會導致失去關聯的命名空間，在叢集上。 因應措施是手動刪除命名空間，才能部署具有相同名稱的叢集。

#### <a name="kubeadm-deployments"></a>kubeadm 部署

如果您要部署多部電腦上的 Kubernetes 使用 kubeadm，叢集系統管理入口網站不會正確顯示連線至巨量資料叢集所需的端點。 如果您遇到這個問題，使用下列因應措施若要探索的服務端點 IP 位址：

- 如果您從連接在叢集內，查詢服務 IP 端點，您想要連線到 Kubernetes。 例如，下列**kubectl**命令會顯示 SQL Server 的主要執行個體的 IP 位址：

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- 如果您從外部連線的叢集，請使用下列步驟來連接：

   1. 取得執行 SQL Server 的主要執行個體的節點的 IP 位址： `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`。

   1. 連接到 SQL Server 使用此 IP 位址的主要執行個體。

   1. 查詢**cluster_endpoint_table**其他外部端點的 master 資料庫中。

      如果失敗連接逾時，就可以在對應的節點進行防火牆處理。 在此情況下，您必須連絡您的 Kubernetes 叢集系統管理員，並要求為對外公開的節點 IP。 這可能是任何節點。 您接著可以使用該 IP 和對應的連接埠連接到叢集中執行的各種服務。 比方說，系統管理員可以執行以尋找此 IP:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="mssqlctlctp23"></a> mssqlctl

- **Mssqlctl**工具變更至名詞動詞命令的順序排序動詞-名詞 」 命令。 例如，`mssqlctl create cluster`現在`mssqlctl cluster create`。

- `--name`參數現在是在建立叢集時所需`mssqlctl cluster create`。

   ```bash
   mssqlctl cluster create --name <cluster_name>
   ```

- 如需升級至最新版的巨量資料叢集的重要資訊和**mssqlctl**，請參閱[升級至新版](deployment-guidance.md#upgrade)。

#### <a name="external-tables"></a>外部資料表

- 可以建立具有不支援的資料行類型為資料表的資料集區外部資料表。 如果您查詢外部資料表時，您收到訊息如下所示：

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 如果您查詢儲存體集區外部資料表時，您可能會發生錯誤，如果在相同的時間基礎檔案複製到 HDFS。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 如果您要建立外部資料表以使用字元資料類型的 Oracle，Azure Data Studio virtualization 精靈會解譯為 VARCHAR 這些資料行中的外部資料表定義。 這會導致外部資料表 DDL 失敗。 請修改使用 NVARCHAR2 類型，或以手動方式建立 EXTERNAL TABLE 陳述式，而不是使用此精靈指定 NVARCHAR 的 Oracle 結構描述。

#### <a name="application-deployment"></a>應用程式部署

- 在呼叫 R、 Python 或 MLeap 應用程式從支援的 RESTful API 時，呼叫會逾時在 5 分鐘內。

#### <a name="spark-and-notebooks"></a>Spark 和 notebook

- POD IP 位址可能變更 Kubernetes 環境中，Pod 重新啟動時。 在案例中，重新啟動主要 pod，Spark 工作階段可能會失敗並`NoRoteToHostException`。 這因為不使用新的 IP 取得重新整理的 JVM 快取的位址。

- 如果您在 Windows 上有已安裝的 Jupyter 和個別的 Python，可能會失敗 Spark notebook。 若要解決此問題，請升級為最新版本的 Jupyter。

- 在筆記本中，如果您按一下**新增文字**命令時，文字資料格會新增 [預覽] 模式，而不是編輯模式。 您可以按一下 [預覽] 圖示，切換至編輯模式和編輯儲存格。

#### <a name="hdfs"></a>HDFS

- 如果您以滑鼠右鍵按一下檔案，以進行預覽，HDFS 中，您可能會看到下列錯誤：

   `Error previewing file: File exceeds max size of 30MB`

   目前沒有任何方法可預覽檔案大於 30 MB 的 Azure Data Studio。

- 不支援對 hdfs-site.xml 變更的 HDFS 組態變更。

#### <a name="security"></a>安全性

- SA_PASSWORD 屬於環境的且可探索 （例如在線傾印檔案）。 您必須在部署之後，重設 SA_PASSWORD 主要執行個體上。 這不是 bug，但安全性步驟。 如需有關如何變更 SA_PASSWORD 的 Linux 容器的詳細資訊，請參閱[變更 SA 密碼](../linux/quickstart-install-connect-docker.md#sapassword)。

- AKS 記錄檔可能包含適用於巨量資料叢集部署的 SA 密碼。

## <a id="ctp22"></a> CTP 2.2 (年 12 月 2018)

下列各節說明的新功能和巨量資料中的叢集 SQL Server 2019 CTP 2.2 的已知的問題。

### <a name="new-features"></a>新增功能

- 使用叢集系統管理員入口網站存取`/portal`(**https://\<ip 位址\>: 30777/入口網站**)。
- 從主要集區服務名稱變更`service-master-pool-lb`並`service-master-pool-nodeport`至`endpoint-master-pool`。
- 新版**mssqlctl**和更新映像。
- 其他錯誤修正和改進功能。

### <a name="known-issues"></a>已知問題

下列各節說明此版本中的限制與已知的問題。

#### <a name="deployment"></a>部署

- 不支援從舊版升級的巨量資料的資料叢集。 您必須備份並刪除任何現有的巨量資料叢集，才能部署最新版本。 如需詳細資訊，請參閱 <<c0> [ 升級到新版](deployment-guidance.md#upgrade)。

- 在部署之後在 AKS 上，您可能會看到部署的下列兩個警告事件。 這兩個事件的已知問題，但它們不會防止您成功部署在 AKS 上的巨量資料叢集。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- 如果巨量資料叢集部署失敗，不會移除相關聯的命名空間。 這可能會導致失去關聯的命名空間，在叢集上。 因應措施是手動刪除命名空間，才能部署具有相同名稱的叢集。

#### <a name="cluster-administration-portal"></a>叢集系統管理入口網站

叢集系統管理入口網站不會顯示 SQL Server 的主要執行個體的端點。 若要尋找主要執行個體的 IP 位址和連接埠，使用下列項目**kubectl**命令：

```
kubectl get svc endpoint-master-pool -n <your-cluster-name>
```

#### <a name="external-tables"></a>外部資料表

- 可以建立具有不支援的資料行類型為資料表的資料集區外部資料表。 如果您查詢外部資料表時，您收到訊息如下所示：

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 如果您查詢儲存體集區外部資料表時，您可能會發生錯誤，如果在相同的時間基礎檔案複製到 HDFS。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark 和 notebook

- POD IP 位址可能變更 Kubernetes 環境中，Pod 重新啟動時。 在案例中，重新啟動主要 pod，Spark 工作階段可能會失敗並`NoRoteToHostException`。 這因為不使用新的 IP 取得重新整理的 JVM 快取的位址。

- 如果您在 Windows 上有已安裝的 Jupyter 和個別的 Python，可能會失敗 Spark notebook。 若要解決此問題，請升級為最新版本的 Jupyter。

- 在筆記本中，如果您按一下**新增文字**命令時，文字資料格會新增 [預覽] 模式，而不是編輯模式。 您可以按一下 [預覽] 圖示，切換至編輯模式和編輯儲存格。

#### <a name="hdfs"></a>HDFS

- 如果您以滑鼠右鍵按一下檔案，以進行預覽，HDFS 中，您可能會看到下列錯誤：

   `Error previewing file: File exceeds max size of 30MB`

   目前沒有任何方法可預覽檔案大於 30 MB 的 Azure Data Studio。

- 不支援對 hdfs-site.xml 變更的 HDFS 組態變更。

#### <a name="security"></a>安全性

- SA_PASSWORD 屬於環境的且可探索 （例如在線傾印檔案）。 您必須在部署之後，重設 SA_PASSWORD 主要執行個體上。 這不是 bug，但安全性步驟。 如需有關如何變更 SA_PASSWORD 的 Linux 容器的詳細資訊，請參閱[變更 SA 密碼](../linux/quickstart-install-connect-docker.md#sapassword)。

- AKS 記錄檔可能包含適用於巨量資料叢集部署的 SA 密碼。

## <a id="ctp21"></a> CTP 2.1 (11 月 2018)

下列各節說明的新功能與 SQL Server 2019 CTP 2.1 中的巨量資料叢集的已知的問題。

### <a name="new-features"></a>新增功能

- [將 Python 和 R 的應用程式部署](big-data-cluster-create-apps.md)巨量資料叢集中。
- 新版**mssqlctl**和更新映像。 
- 其他錯誤修正和改進功能。

### <a name="known-issues"></a>已知問題

下列各節提供 SQL Server CTP 2.1 中的巨量資料叢集已知的問題。

#### <a name="deployment"></a>部署

- 不支援從舊版升級的巨量資料的資料叢集。 您必須備份並刪除任何現有的巨量資料叢集，才能部署最新版本。 如需詳細資訊，請參閱 <<c0> [ 升級到新版](deployment-guidance.md#upgrade)。

- 在部署之後在 AKS 上，您可能會看到部署的下列兩個警告事件。 這兩個事件的已知問題，但它們不會防止您成功部署在 AKS 上的巨量資料叢集。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- 如果巨量資料叢集部署失敗，不會移除相關聯的命名空間。 這可能會導致失去關聯的命名空間，在叢集上。 因應措施是手動刪除命名空間，才能部署具有相同名稱的叢集。

#### <a name="admin-portal"></a>系統管理員入口網站

- 當您[建立應用程式使用 msqlctl ctp 命令](big-data-cluster-create-apps.md)並將其部署巨量資料叢集，叢集系統管理員入口網站顯示 pod 已部署應用程式為 「 不明 」 的 Admin] 部分的 [控制器] 區段中的 SQL Server 上。

#### <a name="external-tables"></a>外部資料表

- 可以建立具有不支援的資料行類型為資料表的資料集區外部資料表。 如果您查詢外部資料表時，您收到訊息如下所示：

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 如果您查詢儲存體集區外部資料表時，您可能會發生錯誤，如果在相同的時間基礎檔案複製到 HDFS。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark 和 notebook

- POD IP 位址可能變更 Kubernetes 環境中，Pod 重新啟動時。 在案例中，重新啟動主要 pod，Spark 工作階段可能會失敗並`NoRoteToHostException`。 這因為不使用新的 IP 取得重新整理的 JVM 快取的位址。

- 如果您在 Windows 上有已安裝的 Jupyter 和個別的 Python，可能會失敗 Spark notebook。 若要解決此問題，請升級為最新版本的 Jupyter。

- 在筆記本中，如果您按一下**新增文字**命令時，文字資料格會新增 [預覽] 模式，而不是編輯模式。 您可以按一下 [預覽] 圖示，切換至編輯模式和編輯儲存格。

#### <a name="hdfs"></a>HDFS

- 如果您以滑鼠右鍵按一下檔案，以進行預覽，HDFS 中，您可能會看到下列錯誤：

   `Error previewing file: File exceeds max size of 30MB`

   目前沒有任何方法可預覽檔案大於 30 MB 的 Azure Data Studio。

- 不支援對 hdfs-site.xml 變更的 HDFS 組態變更。

#### <a name="security"></a>安全性

- SA_PASSWORD 屬於環境的且可探索 （例如在線傾印檔案）。 您必須在部署之後，重設 SA_PASSWORD 主要執行個體上。 這不是 bug，但安全性步驟。 如需有關如何變更 SA_PASSWORD 的 Linux 容器的詳細資訊，請參閱[變更 SA 密碼](../linux/quickstart-install-connect-docker.md#sapassword)。

- AKS 記錄檔可能包含適用於巨量資料叢集部署的 SA 密碼。

## <a id="ctp20"></a> CTP 2.0 (第 2018 年 10 月)

下列各節說明的新功能與 SQL Server 2019 CTP 2.0 中的巨量資料叢集的已知的問題。

### <a name="new-features"></a>新增功能

- 簡單的部署經驗，使用 mssqlctl 管理工具
- 在 Azure 資料 Studio 中的原生的 notebook 體驗
- 查詢存放區執行個體的 SQL 伺服器透過 HDFS 檔案
- 透過 SQL Server、 Oracle、 MongoDB、 和 HDFS 的主要資料虛擬化
- SQL Server 和 Oracle 在 Azure 資料 Studio 中的資料虛擬化精靈
- 在主機上的 ML 服務
- 您可以使用監視和疑難排解的叢集系統管理入口網站
- 在 Azure 資料 Studio 中提交 Spark 作業 
- 在 叢集系統管理入口網站中的 Spark UI
- 磁碟區掛接到儲存體類別
- 透過從主要的資料集區的查詢
- 在 SSMS 中顯示分散式查詢的計的劃
- Pip 套件 mssqlctl 的管理工具
- 透過控制器服務的內建部署引擎

### <a name="known-issues"></a>已知問題

下列各節提供 SQL Server CTP 2.0 中的巨量資料叢集已知的問題。

#### <a name="deployment"></a>部署

- 如果您使用 Azure Kubernetes Service (AKS)，建議的 Kubernetes 版本是 1.10。 *，不支援調整磁碟大小。 您應該要確定您將會據以調整大小的儲存體在部署階段。 如需有關如何調整儲存體大小的詳細資訊，請參閱 <<c0> [ 資料持續性](concept-data-persistence.md)文章。 針對部署在 Vm 上的 Kubernetes，建議的版本是 1.11。

- 在部署之後在 AKS 上，您可能會看到部署的下列兩個警告事件。 這兩個事件的已知問題，但它們不會防止您成功部署在 AKS 上的巨量資料叢集。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- 如果巨量資料叢集部署失敗，不會移除相關聯的命名空間。 這可能會導致失去關聯的命名空間，在叢集上。 因應措施是手動刪除命名空間，才能部署具有相同名稱的叢集。

#### <a name="external-tables"></a>外部資料表

- 可以建立具有不支援的資料行類型為資料表的資料集區外部資料表。 如果您查詢外部資料表時，您收到訊息如下所示：

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 如果您查詢儲存體集區外部資料表時，您可能會發生錯誤，如果在相同的時間基礎檔案複製到 HDFS。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark 和 notebook

- POD IP 位址可能變更 Kubernetes 環境中，Pod 重新啟動時。 在案例中，重新啟動主要 pod，Spark 工作階段可能會失敗並`NoRoteToHostException`。 這因為不使用新的 IP 取得重新整理的 JVM 快取的位址。

- 如果您在 Windows 上有已安裝的 Jupyter 和個別的 Python，可能會失敗 Spark notebook。 若要解決此問題，請升級為最新版本的 Jupyter。

- 在筆記本中，如果您按一下**新增文字**命令時，文字資料格會新增 [預覽] 模式，而不是編輯模式。 您可以按一下 [預覽] 圖示，切換至編輯模式和編輯儲存格。

#### <a name="hdfs"></a>HDFS

- 如果您以滑鼠右鍵按一下檔案，以進行預覽，HDFS 中，您可能會看到下列錯誤：

   `Error previewing file: File exceeds max size of 30MB`

   目前沒有任何方法可預覽檔案大於 30 MB 的 Azure Data Studio。

- 不支援對 hdfs-site.xml 變更的 HDFS 組態變更。

#### <a name="security"></a>安全性

- SA_PASSWORD 屬於環境的且可探索 （例如在線傾印檔案）。 您必須在部署之後，重設 SA_PASSWORD 主要執行個體上。 這不是 bug，但安全性步驟。 如需有關如何變更 SA_PASSWORD 的 Linux 容器的詳細資訊，請參閱[變更 SA 密碼](../linux/quickstart-install-connect-docker.md#sapassword)。

- AKS 記錄檔可能包含適用於巨量資料叢集部署的 SA 密碼。

## <a name="next-steps"></a>後續步驟

如需有關 SQL Server 的巨量資料叢集的詳細資訊，請參閱 <<c0> [ 什麼是 SQL Server 2019 巨量資料叢集？](big-data-cluster-overview.md)。
