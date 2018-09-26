---
title: 如何設定 Linux 上的 SQL Server 持續性記憶體 (PMEM) |Microsoft Docs
description: 這篇文章提供逐步解說在 Linux 上設定 PMEM。
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 42b51f28682ea7c53b5aa6f33ac2e6aa61a121ed
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46714956"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>如何設定 Linux 上的 SQL Server 持續性記憶體 (PMEM)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

本文說明如何設定 Linux 上的 SQL Server 持續性記憶體 (PMEM)。 Linux 上的 PMEM 支援是在 SQL Server 2019 CTP 2.0 引進。

## <a name="overview"></a>概觀

SQL Server 2016 導入靜態的 Dimm、 支援及最佳化稱為[NVDIMM-N 上的記錄檔快取結尾]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/)，縮短的強化記錄緩衝區永續性儲存體所需的作業數量。 這會運用 Windows Server 能夠直接存取持續性記憶體裝置，在 DAX 的模式。

SQL Server 2019 預覽會擴充持續性記憶體的支援 Linux (PMEM) 裝置提供完整啟蒙置於 PMEM 的資料和交易記錄檔。 啟蒙指的是存取的使用有效的使用者空間 memcpy 作業的儲存體裝置權的方法。 而不是透過檔案系統和儲存體堆疊，SQL Server 會利用將直接將資料放入裝置，不會產生最少的延遲到 Linux 上的 DAX 支援。

## <a name="enable-enlightenment-of-database-files"></a>啟用啟蒙的資料庫檔案
若要啟用啟蒙的 Linux 上 SQL Server 中的資料庫檔案，請遵循下列步驟：

1. 設定裝置在 Linux 中，這是使用`ndctl`公用程式。

  - 安裝安裝`ndctl`設定 pmem 裝置。 您可以找到它[此處](https://docs.pmem.io/getting-started-guide/installing-ndctl)。
  - 您可以使用 [ndctl] 來建立命名空間。

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* –map=mem
  ```

  >[!NOTE]
  >如果您使用`ndctl`版本低於 59，使用`--mode=memory`。

  使用`ndctl`確認命名空間。 範例輸出如下所示：

```bash
ndctl list
[
  {
    "dev":"namespace0.0",
    "mode":"memory",
    "size":1099511627776,
    "blockdev":"pmem0",
    "numa_node":0
  }
]
```

  - 建立和掛接 pmem 裝置

    例如，使用 XFS

    ```bash
    mkfs.xfs -f /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    例如，對於 EXT4

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    ```

  一旦裝置已設有 ndctl、 格式化和掛接，您就可以在其中放置資料庫檔案。 您也可以建立新的資料庫 

1. 使用追蹤旗標 3979，以啟用 SQL Server 資料庫檔案啟蒙。 此追蹤旗標啟動追蹤旗標，並因此需要使用 mssql conf 公用程式來啟用。

1. 重新啟動 SQL Server。

## <a name="next-steps"></a>後續步驟

在 Linux 上 SQL Server 的相關資訊，請參閱[在 Linux 上的 SQL Server](sql-server-linux-overview.md)。
