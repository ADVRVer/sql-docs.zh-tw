---
title: 使用 curl 將資料載入 HDFS | Microsoft Docs
titleSuffix: SQL Server big data clusters
description: 使用 curl 將資料載入至 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] 上的 HDFS。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 970c4f51535395a940a9c47e77d864d00c1f403c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "73706625"
---
# <a name="use-curl-to-load-data-into-hdfs-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>使用 curl 將資料載入至 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] 上的 HDFS

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

本文說明如何使用 **curl** 將資料載入至 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]上的 HDFS。

## <a id="prereqs"></a> 必要條件

- [將範例資料載入巨量資料叢集](tutorial-load-sample-data.md)

## <a name="obtain-the-service-external-ip"></a>取得服務外部 IP

當部署完成時會啟動 WebHDFS，並透過 Knox 進行存取。 Knox 端點是透過名為 **gateway-svc-external** 的 Kubernetes 服務公開。  若要建立必要的 WebHDFS URL 來上傳/下載檔案，您需要 **gateway-svc-external** 服務外部 IP 位址和巨量資料叢集的名稱。 您可以執行下列命令，取得 **gateway-svc-external** 服務外部 IP 位址：

```bash
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> 這裡的 `<big data cluster name>` 是您在部署組態檔中指定的叢集名稱。 預設名稱為 `mssql-cluster`。

## <a name="construct-the-url-to-access-webhdfs"></a>建構 URL 來存取 WebHDFS

現在，您可以建構 URL 來存取 WebHDFS，如下所示：

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

例如：

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>列出檔案

若要列出 **hdfs:///product_review_data** 底下的檔案，請使用下列 curl 命令：

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>將本機檔案放入 HDFS

若要將新檔案 **test.csv** 從本機目錄放到 product_review_data 目錄，請使用下列 curl 命令 (**Content-Type** 是必要參數)：

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>建立目錄

若要在 **下建立目錄**test`hdfs:///`，請使用下列命令：

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>後續步驟

如需 SQL Server 巨量資料叢集的詳細資訊，請參閱[什麼是 SQL Server 巨量資料叢集](big-data-cluster-overview.md)。
