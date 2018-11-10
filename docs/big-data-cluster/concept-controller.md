---
title: 什麼是 SQL Server 的巨量資料叢集控制器？ | Microsoft Docs
description: 本文說明 SQL Server 2019 巨量資料叢集的控制站。
author: mihaelablendea
ms.author: mihaelab
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: abf8c174379ad444cd29b5115240ad7c404b2c4b
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221514"
---
# <a name="what-is-the-sql-server-big-data-clusters-controller"></a>什麼是 SQL Server 的巨量資料叢集控制站？

控制站會裝載部署及管理巨量資料叢集的核心邏輯。 它會負責與 Kubernetes 叢集與 HDFS 和 Spark 等其他元件的一部分的 SQL Server 執行個體的所有互動。 

控制器服務提供核心功能如下：

- 管理叢集生命週期： 叢集啟動程序與刪除、 更新組態
- 管理主要的 SQL Server 執行個體
- 管理計算、 資料和儲存體集區
- 若要觀察的叢集狀態的監視工具公開 （expose)
- 公開 （expose) 來偵測並修復未預期的問題的疑難排解工具
- 管理叢集安全性： 確保安全的叢集端點、 管理使用者和角色、 設定叢集間通訊的認證
- 管理升級的工作流程，以便安全地實作 （不適用於 CTP 2.1）
- （不適用於 CTP 2.1） 叢集中具狀態服務的管理高可用性和 DR

## <a name="deploying-the-controller-service"></a>部署控制器服務

控制器會部署並裝載於相同的客戶，想要建置巨量資料叢集的 Kubernetes 命名空間。 此服務管理員安裝的 Kubernetes 叢集啟動程序，使用 mssqlctl 命令列公用程式期間：

```bash
mssqlctl create cluster <name of your cluster>
```

增建工作流程會在 Kubernetes 上的版面配置功能完整的 SQL Server 巨量資料叢集，其中包含所述的所有元件[概觀](big-data-cluster-overview.md)文章。 啟動程序的工作流程首先會建立控制器服務，以及安裝和設定的主機、 計算、 資料和儲存體集區的服務一部分的其餘部分，這部署之後，將協調控制器服務。

## <a name="managing-the-cluster-through-the-controller-service"></a>管理透過控制器服務叢集
您可以管理純粹是透過使用控制器服務在叢集`mssqlctl`Api 或裝載於叢集內的叢集系統管理入口網站。 如果您將其他像是 pod 的 Kubernetes 物件部署到相同的命名空間時，不受管理或監視的控制器服務。

建立適用於巨量資料叢集的 Kubernetes 物件 （可設定狀態的集合，pod、 密碼等） 和的控制站位於專用的 Kubernetes 命名空間。 控制器服務將 Kubernetes 叢集系統管理員可以管理該命名空間內的所有資源授與權限。  在初始叢集部署使用自動設定此案例中的 RBAC 原則`mssqlctl`。 

### <a name="mssqlctl"></a>mssqlctl

`mssqlctl` 命令列公用程式是以 Python，可讓叢集系統管理員啟動及管理巨量資料叢集透過控制器服務所公開的 REST Api 撰寫。

### <a name="cluster-administration-portal"></a>叢集系統管理入口網站

一旦在控制器服務已啟動並執行，叢集系統管理員可以使用叢集系統管理員入口網站來監視部署進度、 偵測，以及針對在叢集內的服務問題進行疑難排解。 

## <a name="monitoring-and-troubleshooting-the-controller-service"></a>監視和疑難排解控制器服務

即將推出...

## <a name="controller-service-security"></a>控制器服務的安全性
Controller 服務的所有通訊是透過 REST API 都進行 HTTPS。 自我簽署的憑證將會自動產生為您在啟動程序時之用。 

控制器服務端點的驗證根據使用者名稱和密碼。 這些認證會在叢集啟動程序時使用環境變數的輸入佈建`CONTROLLER_USERNAME`和`CONTROLLER_PASSWORD`。
```

> [!NOTE]
> You must provide a password that is in compliance with [SQL Server password complexity requirements](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## Next steps

To learn more about the SQL Server big data clusters, see the following overview:

- [What are SQL Server 2019 big data clusters?](big-data-cluster-overview.md)
