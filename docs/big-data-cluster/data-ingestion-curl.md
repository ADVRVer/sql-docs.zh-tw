---
title: 使用 curl 將資料載入 HDFS |Microsoft Docs
titleSuffix: SQL Server big data clusters
description: 將資料載入 HDFS，在 SQL Server 2019 巨量資料叢集上使用 curl。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 56bee3241427b9de9768e7bdd9e49646b51521d1
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59947794"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-big-data-clusters"></a>將資料載入 HDFS，在 SQL Server 的巨量資料叢集上使用 curl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

這篇文章說明如何使用**curl**將資料載入 SQL Server 2019 巨量資料叢集 （預覽） 上的 HDFS。

## <a name="obtain-the-service-external-ip"></a>取得服務的外部 IP

當部署完成之後，且其存取權會經歷 Knox 時，會啟動 WebHDFS。 Knox 端點透過名為的 Kubernetes 服務公開**端點安全性**。  若要建立必要的 WebHDFS URL，來上傳/下載檔案，您需要**端點安全性**服務外部 IP 位址和您的叢集名稱。 您可以取得**端點安全性**服務外部 IP 位址執行下列命令：

```bash
kubectl get service endpoint-security -n <cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<cluster name>`以下是您在執行時所提供的叢集名稱`mssqlctl cluster create --name <cluster name>`。

## <a name="construct-the-url-to-access-webhdfs"></a>建構的 URL 來存取 WebHDFS

現在，您可以建構 URL 才能存取 WebHDFS，如下所示：

`https://<endpoint-security service external IP address>:30443/gateway/default/webhdfs/v1/`

例如：

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>列出檔案

清單下的檔案**hdfs: / / airlinedata**，使用下列 curl 命令：

```bash
curl -i -k -u root:root-password -X GET 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>將本機檔案放到 HDFS

若要將新的檔案**test.csv** airlinedata 目錄的本機目錄，使用下列 curl 命令 ( **Content-type**是必要參數):

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>建立目錄

若要建立目錄**測試**下方`hdfs:///`，使用下列命令：

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>後續步驟

如需有關 SQL Server 的巨量資料叢集的詳細資訊，請參閱[什麼是 SQL Server 的巨量資料叢集？](big-data-cluster-overview.md)。
