---
title: 使用 curl 將資料載入 HDFS | Microsoft Docs
titleSuffix: SQL Server big data clusters
description: 使用 curl 將資料載入 SQL Server 2019 巨量資料叢集上的 HDFS。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ae893bb1e291b244b5101ccfb2ed66bcf765f049
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91866845"
---
# <a name="use-curl-to-load-data-into-hdfs-on-big-data-clusters-2019"></a>使用 curl 將資料載入至 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] 上的 HDFS

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

本文說明如何使用 **curl** 將資料載入至 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]上的 HDFS。

## <a name="prerequisites"></a><a id="prereqs"></a> 必要條件

- [將範例資料載入巨量資料叢集](tutorial-load-sample-data.md)

## <a name="obtain-the-service-external-ip"></a>取得服務外部 IP

當部署完成時會啟動 WebHDFS，並透過 Knox 進行存取。 Knox 端點是透過名為 **gateway-svc-external** 的 Kubernetes 服務公開。  若要建立必要的 WebHDFS URL 來上傳/下載檔案，您需要 **gateway-svc-external** 服務外部 IP 位址和巨量資料叢集的名稱。 您可以執行下列命令，取得 **gateway-svc-external** 服務外部 IP 位址：

```terminal
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> 這裡的 `<big data cluster name>` 是您在部署組態檔中指定的叢集名稱。 預設名稱為 `mssql-cluster`。

## <a name="construct-the-url-to-access-webhdfs"></a>建構 URL 來存取 WebHDFS

現在，您可以建構 URL 來存取 WebHDFS，如下所示：

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

例如：

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="authentication-with-active-directory"></a>使用 Active Directory 驗證

針對使用 Active Directory 的部署，請使用具有 `curl` 的驗證參數來配合交涉驗證。 

若要使用 `curl` 搭配 Active Directory 驗證，請執行此命令：

```
kinit <username>
```

命令會產生 Kerberos 權杖供 `curl` 使用。 下節示範的命令會指定 `curl` 的 `--anyauth` 參數。 對於需要交涉驗證的 URL，`curl` 會自動偵測並使用產生的 Kerberos 權杖向 URL 驗證，而不是使用者名稱和密碼。

## <a name="list-a-file"></a>列出檔案

若要列出 **hdfs:///product_review_data** 底下的檔案，請使用下列 curl 命令：

```terminal
curl -i -k --anyauth -u root:<AZDATA_PASSWORD> -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]

針對不是使用 root 的端點，請使用下列 curl 命令：

```terminal
curl -i -k --anyauth -u <AZDATA_USERNAME>:<AZDATA_PASSWORD> -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>將本機檔案放入 HDFS

若要將新檔案 **test.csv** 從本機目錄放到 product_review_data 目錄，請使用下列 curl 命令 (**Content-Type** 是必要參數)：

```terminal
curl -i -L -k --anyauth -u root:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]

針對不是使用 root 的端點，請使用下列 curl 命令：

```terminal
curl -i -L -k --anyauth -u <AZDATA_USERNAME>:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>建立目錄

若要在 `hdfs:///` 下建立目錄 **test**，請使用下列命令：

```terminal
curl -i -L -k --anyauth -u root:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]
針對不是使用 root 的端點，請使用下列 curl 命令：

```terminal
curl -i -L -k --anyauth -u <AZDATA_USERNAME>:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>後續步驟

如需 SQL Server 巨量資料叢集的詳細資訊，請參閱[什麼是 SQL Server 巨量資料叢集](big-data-cluster-overview.md)。
