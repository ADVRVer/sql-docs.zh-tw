---
title: 何謂存放集區？
titleSuffix: SQL Server 2019 big data clusters
description: 本文說明 SQL Server 2019 巨量資料叢集存放集區。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: c0f376066ad02e70576c59bfe13c6f77e4b72c09
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53029952"
---
# <a name="what-is-the-storage-pool-sql-server-2019-big-data-clusters"></a>何謂存放集區 （SQL Server 2019 巨量資料叢集）

本文說明所扮演的角色*SQL Server 儲存體集區*在 SQL Server 2019 巨量資料叢集 （預覽） 中。 下列各節描述的架構和功能的 SQL 儲存體集區。

## <a name="storage-pool-architecture"></a>儲存體集區架構

存放集區是由節點組成 SQL Server on Linux、 Spark 和 HDFS 的儲存體所組成。 在 SQL 巨量資料叢集中的所有存放裝置節點是 HDFS 叢集的成員。

![儲存體集區架構](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>責任

儲存體節點會負責：

- 透過 Spark 的資料擷取。
- HDFS （Parquet 格式） 中的資料存放區。 HDFS 也會提供資料持續性，因為 HDFS 資料會分散儲存體叢集中所有節點 SQL 巨量資料。
- 透過 HDFS 與 SQL Server 端點的資料存取。

## <a name="next-steps"></a>後續步驟

若要深入了解 SQL Server 巨量資料叢集，請參閱下列概觀：

- [什麼是 SQL Server 2019 巨量資料叢集？](big-data-cluster-overview.md)
