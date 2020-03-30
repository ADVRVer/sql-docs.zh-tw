---
title: 設定讀取級別可用性群組 (Linux 上的 SQL Server)
description: 了解如何設定 SQL Server Always On 可用性群組 (AG)，供 Linux 上的讀取級別工作負載使用。
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 1ce63521989edfccc1fc9fc085b0a9c476cde2ee
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "75558392"
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-linux"></a>設定 SQL Server 可用性群組供 Linux 上的讀取級別使用

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

您可以設定 SQL Server Always On 可用性群組 (AG)，供 Linux 上的讀取級別工作負載使用。 AG 有兩種結構類型。 高可用性結構會使用叢集管理員來確保改善的商務持續性。 此結構亦可包含讀取級別複本。 若要建立高可用性結構，請參閱[設定 SQL Server Always On 可用性群組以確保 Linux 上的高可用性](sql-server-linux-availability-group-configure-ha.md)。 其他結構僅支援讀取級別工作負載。 本文說明如何建立不使用叢集管理員的 AG，供讀取級別工作負載之用。 此結構只會提供讀取級別。 它不會提供高可用性。

> [!NOTE]
> `CLUSTER_TYPE = NONE` 的可用性群組可包含裝載於不同作業系統平台上的複本。 它無法支援高可用性。 

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>建立 AG

建立 AG。 設定 `CLUSTER_TYPE = NONE`。 此外，將每個複本設定為 `FAILOVER_MODE = MANUAL`。 執行分析或報告工作負載的用戶端應用程式可以直接連線到次要資料庫。 您也可以建立唯讀路由清單。 連線到主要複本會從路由清單，以循環配置資源的方式將讀取連線要求轉送至每個次要複本。

下列 Transact-SQL 指令碼會建立名為 `ag1` 的 AG。 該指令碼會將 AG 複本設定為 `SEEDING_MODE = AUTOMATIC`。 此設定會使 SQL Server 在新增至 AG 之後，在每個次要伺服器上自動建立資料庫。 更新您環境中的下列指令碼。 將 `<node1>` 和 `<node2>` 值取代為裝載複本之 SQL Server 執行個體的名稱。 將 `<5022>` 值取代為您為端點設定的連接埠。 在 SQL Server 主要複本上，執行下列 TRANSACT-SQL 指令碼：

```SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'<node1>' WITH (
            ENDPOINT_URL = N'tcp://<node1>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'<node2>' WITH ( 
            ENDPOINT_URL = N'tcp://<node2>:<5022>', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-ag"></a>將次要 SQL Server 加入 AG

下列 Transact-SQL 指令碼會將伺服器加入名為 `ag1` 的 AG。 更新您環境中的指令碼。 在每個 SQL Server 次要複本上，執行下列 TRANSACT-SQL 指令碼以加入 AG：

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

此 AG 不是高可用性設定。 如果您需要高可用性，請遵循[為 Linux 上的 SQL Server 設定 Always On 可用性群組](sql-server-linux-availability-group-configure-ha.md)中的指示進行。 具體而言，請建立 `CLUSTER_TYPE=WSFC` (Windows) 或 `CLUSTER_TYPE=EXTERNAL` (Linux) 的 AG。 接著，使用 Windows 的 Windows Server 容錯移轉叢集或 Linux 的 Pacemaker 來整合叢集管理員。

## <a name="connect-to-read-only-secondary-replicas"></a>連線到唯讀次要複本

有兩種方式可連線到唯讀次要複本。 應用程式可以直接連線到裝載次要複本的 SQL Server 執行個體，並查詢資料庫。 它們也可以使用唯讀路由，這需要接聽程式。

* [可讀取的次要複本](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [唯讀路由](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>容錯移轉讀取級別可用性群組上的主要複本

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>後續步驟

* [設定分散式可用性群組](../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)
* [深入了解可用性群組](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
* [執行強制手動容錯移轉](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)
