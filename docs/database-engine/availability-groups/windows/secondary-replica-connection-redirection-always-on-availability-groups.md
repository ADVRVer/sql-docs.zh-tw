---
title: 將讀取/寫入連線重新導向至主要複本
description: 了解如何一律將讀取/寫入連線重新導向至 Always On 可用性群組的主要複本，無論連接字串中所指定的目標伺服器為何。
ms.custom: seo-lt-2019
ms.date: 01/09/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: article
helpviewer_keywords:
- connection access to availability replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], readable secondary replicas
- active secondary replicas [SQL Server], read-only access to
- readable secondary replicas
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cb7ac494a8a87b0ac5f2f6692763d526b7f26af6
ms.sourcegitcommit: 49082f9b6b3bc8aaf9ea3f8557f40c9f1b6f3b0b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77256661"
---
# <a name="secondary-to-primary-replica-readwrite-connection-redirection-always-on-availability-groups"></a>次要到主要複本讀取/寫入連線重新導向 (Always On 可用性群組)

[!INCLUDE[appliesto](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)] CTP 2.0 引進 Always On 可用性群組的*次要到主要複本讀取/寫入連線重新導向*。 任何作業系統平台上都可以使用讀取/寫入連線重新導向。 它允許將用戶端應用程式連線導向至主要複本，而不論連接字串中指定的目標伺服器為何。 

例如，連接字串可以將目標設為次要複本。 根據可用性群組 (AG) 複本的設定以及連接字串中的設定，可以將連線自動重新導向至主要複本。 

## <a name="use-cases"></a>使用案例

在 [!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)] 之前，AG 接聽程式和對應的叢集資源會將使用者流量重新導向至主要複本，確保容錯移轉之後的重新連線。 [!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)] 會繼續支援 AG 接聽程式功能，並針對不能包含接聽程式的情節新增複本連線重新導向。 例如：

* SQL Server 可用性群組與其整合的叢集技術未提供功能這類接聽程式 
* 多子網路設定 (例如在雲端或含 Pacemaker 的多子網路浮動 IP)，其中，設定變得複雜、容易發生錯誤，並且因包含多元件而難以疑難排解
* 閱讀向外延展或災害復原，而且叢集類型為 `NONE`，因為沒有直接機制可確保手動容錯移轉時的透明重新連線

## <a name="requirement"></a>需求

讓次要複本重新導向讀取/寫入連線要求：
* 次要複本必須為線上。 
* 複本規格 `PRIMARY_ROLE` 必須包含 `READ_WRITE_ROUTING_URL`。
* 連接字串必須是 `ReadWrite`，可透過將 `ApplicationIntent` 定義為 `ReadWrite`，或不設定 `ApplicationIntent` 並讓預設值 (`ReadWrite`) 生效來完成。

## <a name="set-read_write_routing_url-option"></a>設定 READ_WRITE_ROUTING_URL 選項

若要設定讀取/寫入連線重新導向，請在建立 AG 時設定主要複本的 `READ_WRITE_ROUTING_URL`。 

在 [!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)] 中，已將 `READ_WRITE_ROUTING_URL` 新增至 `<add_replica_option>` 規格。 請參閱下列主題： 

* [CREATE AVAILABILITY GROUP](../../../t-sql/statements/create-availability-group-transact-sql.md)
* [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md)


### <a name="primary_roleread_write_routing_url-not-set-default"></a>未設定 PRIMARY_ROLE(READ_WRITE_ROUTING_URL) (預設) 

根據預設，未設定複本的讀取/寫入複本連線重新導向。 次要複本處理連線要求的方式取決於次要複本是否設定為允許連線，以及連接字串中的 `ApplicationIntent` 設定是否設定為允許連線。 下表顯示次要複本如何根據 `SECONDARY_ROLE (ALLOW CONNECTIONS = )` 和 `ApplicationIntent` 來處理連線。

||`SECONDARY_ROLE (ALLOW CONNECTIONS = NO)`|`SECONDARY_ROLE (ALLOW CONNECTIONS = READ_ONLY)`|`SECONDARY_ROLE (ALLOW CONNECTIONS = ALL)`|
|-----|-----|-----|-----|
|`ApplicationIntent=ReadWrite`<br/> 預設|連線失敗|連線失敗|連線成功<br/>讀取成功<br/>寫入失敗|
|`ApplicationIntent=ReadOnly`|連線失敗|連線成功|連線成功

上表顯示預設行為，其與 [!INCLUDE[sssqlv15-md](../../../includes/sssqlv15-md.md)] 之前的 SQL Server 版本相同。 

### <a name="primary_roleread_write_routing_url-set"></a>設定 PRIMARY_ROLE(READ_WRITE_ROUTING_URL) 

在您設定讀取/寫入連線重新導向之後，複本處理連線要求的方式可能會不同。 連線行為仍然取決於 `SECONDARY_ROLE (ALLOW CONNECTIONS = )` 和 `ApplicationIntent` 設定。 下表顯示已設定 `READ_WRITE_ROUTING` 的次要複本如何根據 `SECONDARY_ROLE (ALLOW CONNECTIONS = )` 和 `ApplicationIntent` 來處理連線。

||`SECONDARY_ROLE (ALLOW CONNECTIONS = NO)`|`SECONDARY_ROLE (ALLOW CONNECTIONS = READ_ONLY)`|`SECONDARY_ROLE (ALLOW CONNECTIONS = ALL)`|
|-----|-----|-----|-----|
|`ApplicationIntent=ReadWrite`<br/>預設|連線失敗|連線失敗|與主要的連線路由|
|`ApplicationIntent=ReadOnly`|連線失敗|連線成功|連線成功

上表顯示如果主要複本已設定 `READ_WRITE_ROUTING_URL`，則次要複本會在 `SECONDARY_ROLE (ALLOW CONNECTIONS = ALL)` 而且連線指定 `ReadWrite` 時將連線重新導向至主要複本。

## <a name="example"></a>範例 

在此範例中，可用性群組會有三個複本：
* COMPUTER01 上的主要複本
* COMPUTER02 上的同步次要複本
* COMPUTER03 上的非同步次要複本

下圖代表可用性群組。

![原始可用性群組](media/replica-connection-redirection-always-on-availability-groups/01_originalAG.png)

下列 Transact-SQL 指令碼會建立此 AG。 在此範例中，每個複本都會指定 `READ_WRITE_ROUTING_URL`。
```sql
CREATE AVAILABILITY GROUP MyAg   
     WITH ( CLUSTER_TYPE =  NONE )  
   FOR   
     DATABASE  <Database1>   
   REPLICA ON   
      'COMPUTER01' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01.<domain>.<tld>:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = MANUAL,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER01.<domain>.<tld>:1433' ),
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER02, COMPUTER03),
            READ_WRITE_ROUTING_URL = 'TCP://COMPUTER01.<domain>.<tld>:1433' )   
         SESSION_TIMEOUT = 10  
         ),   
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02.<domain>.<tld>:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = MANUAL, 
         SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER02.<domain>.<tld>:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER01, COMPUTER03),  
            READ_WRITE_ROUTING_URL = 'TCP://COMPUTER02.<domain>.<tld>:1433' )   
         SESSION_TIMEOUT = 10  
         ),   
      'COMPUTER03' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03.<domain>.<tld>:5022',  
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = MANUAL,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER03.<domain>.<tld>:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER01, COMPUTER02),  
            READ_WRITE_ROUTING_URL = 'TCP://COMPUTER03.<domain>.<tld>:1433' )  
         SESSION_TIMEOUT = 10  
         );
GO  
```
   - `<domain>.<tld>`
      - 完整網域名稱的網域和頂層網域。 例如： `corporation.com` 。


### <a name="connection-behaviors"></a>連線行為

在下圖中，用戶端應用程式會使用 `ApplicationIntent=ReadWrite` 連線至 COMPUTER02。 連線會重新導向至主要複本。 

![原始可用性群組](media/replica-connection-redirection-always-on-availability-groups/02_redirectionAG.png)

次要複本會將讀取/寫入呼叫重新導向至主要複本。 與任一複本的讀取/寫入連線將會重新導向至主要複本。 

在下圖中，已將主要複本手動容錯移轉至 COMPUTER02。 用戶端應用程式會使用 `ApplicationIntent=ReadWrite` 連線至 COMPUTER01。 連線會重新導向至主要複本。 

![原始可用性群組](media/replica-connection-redirection-always-on-availability-groups/03_redirectionAG.png)


## <a name="sql-server-instance-offline"></a>SQL Server 執行個體離線

如果連接字串中指定的 SQL Server 執行個體無法使用 (發生中斷)，則不論目標伺服器上的複本所扮演的角色為何，連線都會失敗。 若要避免長時間應用程式關閉，請在連接字串中設定替代 `FailoverPartner`。 應用程式必須實作重試邏輯，以容納在實際容錯移轉期間未上線的主要和次要複本。 如需連接字串的詳細資訊，請參閱 [SqlConnection.ConnectionString 屬性](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx)。

## <a name="see-also"></a>另請參閱

[AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 
[關於可用性複本的用戶端連接存取 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)   

[可用性群組接聽程式、用戶端連線及應用程式容錯移轉 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md) 
