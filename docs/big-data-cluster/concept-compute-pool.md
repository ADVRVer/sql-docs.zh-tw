---
title: 計算集區有哪些？
titleSuffix: SQL Server 2019 big data clusters
description: 本文說明在 SQL Server 2019 巨量資料叢集 （預覽） 中的計算集區。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 272f10cfed8f7cd1b07633b81642323a8c74b6d7
ms.sourcegitcommit: 56fb7b648adae2c7b81bd969de067af1a2b54180
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57227130"
---
# <a name="what-are-compute-pools-in-a-sql-server-2019-big-data-cluster"></a>在 SQL Server 2019 巨量資料叢集的計算集區有哪些？

本文說明所扮演的角色*SQL Server 計算集區*中 SQL Server 2019 預覽巨量資料叢集。 計算集區提供的巨量資料叢集相應放大計算資源。 下列各節描述的架構和計算集區的功能。

## <a name="compute-pool-architecture"></a>計算集區架構

計算集區由一個或多個運算在 Kubernetes 中執行的 pod。 自動的建立和管理這些 pod 由協調[SQL Server 的主要執行個體](concept-master-instance.md)。 每個 pod 包含一組基底的服務和 SQL Server database engine 執行個體。

## <a name="scale-out-groups"></a>向外延展群組

在不同的資料來源，例如 HDFS、 Oracle、 MongoDB 或 Terradata，計算集區可做為 PolyBase 向外延展群組的分散式查詢。 使用 Kubernetes 中的計算 pod，巨量資料叢集可以自動建立和設定 PolyBase 向外延展群組的計算 pod。

## <a name="next-steps"></a>後續步驟

若要深入了解 SQL Server 巨量資料叢集，請參閱下列概觀：

- [什麼是 SQL Server 2019 巨量資料叢集？](big-data-cluster-overview.md)
