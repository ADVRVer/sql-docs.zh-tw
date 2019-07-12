---
title: 在 Linux 上設定快照集資料夾共用 SQL Server 複寫
description: 本文說明如何在 Linux 上設定的快照集資料夾共用 SQL Server 複寫。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 456163bfec2324394455a5d098ef01c22d994696
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834798"
---
# <a name="configure-replication-with-non-default-ports"></a>使用非預設連接埠設定複寫

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

在任何使用 network.tcpport mssql conf 設定進行設定的連接埠上接聽的 Linux 執行個體上，您可以使用 SQL Server 設定複寫。 連接埠必須以附加至的伺服器名稱在組態期間如果下列條件成立：

1. 複寫設定牽涉到在 Linux 上的 SQL Server 的執行個體
2. （Windows 或 Linux） 的任何執行個體在非預設連接埠上接聽。 

執行個體的伺服器名稱可由執行 @@servername執行個體上。

## <a name="examples"></a>範例

在 Linux 上的通訊埠 1500年 'Server1' 接聽。 若要設定發佈 'Server1'，執行`sp_adddistributor`與`@distributor`。 例如: 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

在 Linux 上的通訊埠 1500年 'Server1' 接聽。 若要設定為散發者的發行者，執行`sp_adddistpublisher`與`@publisher`。 例如:

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

在 Linux 上的連接埠 6549 'Server2' 接聽。 若要設定 'Server2' 做為訂閱者，請執行`sp_addsubscription`與`@subscriber`。 例如:

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

'Server3' 接聽 Server3 伺服器名稱和執行個體名稱 MSSQL2017 的連接埠 6549 在 Windows 上。 若要設定 'Server3' 做為訂閱者，請執行`sp_addsubscription`與`@subscriber`。 例如:

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>後續步驟

[概念：在 Linux 上的 SQL Server 複寫](sql-server-linux-replication.md)

[複寫預存程序](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)。

