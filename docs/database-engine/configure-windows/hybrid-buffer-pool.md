---
title: 混合式緩衝集區 | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ''
author: DBArgenis
ms.author: argenisf
manager: jroth
ms.openlocfilehash: ce63196cb8a5c8791eb6440f69cf06194591f422
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66785292"
---
# <a name="hybrid-buffer-pool"></a>混合式緩衝集區
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

混合式緩衝集區可讓資料庫引擎直接存取儲存在持續性記憶體 (PMEM) 裝置之資料庫檔案中的資料頁面。 這項功能是在 [!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)] 中引進。

在沒有 PMEM 的傳統系統中，SQL Server 會在 DRAM 型的緩衝集區中快取資料頁。 使用混合式緩衝集區，SQL Server 會略過執行頁面複本，進入緩衝集區的 DRAM 型部分。 改為直接在 PMEM 裝置的資料庫檔案中存取頁面。 存取混合式緩衝集區 PMEM 裝置上的資料檔案，是使用記憶體對應 I/O (MMIO) 執行，也稱為 SQL Server 中的資料檔案「啟用」。

只有完整分頁才能直接在 PMEM 裝置上存取。 頁面標示為中途時，它會先複製到 DRAM 型的緩衝集區，最後再寫回 PMEM 裝置，並再次標示為完整。 此程序是發生在一般檢查點作業期間的狀況。

Windows 和 Linux 都提供混合式緩衝集區功能。 PMEM 裝置必須以支援 DAX (DirectAccess) 的檔案系統格式化。 XFS、EXT4 和 NTFS 檔案系統都支援 DAX。 SQL Server 會自動偵測資料檔案是否位於正確格式化的 PMEM 裝置中，並在使用者空間中執行記憶體對應。 當附加、還原、建立新的資料庫，或啟用資料庫的混合式緩衝集區功能時，此對應就會在啟動時發生。

如需 PMEM 的 Windows Server 支援詳細資訊，請參閱[在 Windows Server 上部署持續性記憶體](/windows-server/storage/storage-spaces/deploy-pmem/)。

如需針對 PMEM 裝置在 Linux 上設定 SQL Server，請參閱[部署持續性記憶體](../../linux/sql-server-linux-configure-pmem.md)。

## <a name="enable-hybrid-buffer-pool"></a>啟用混合式緩衝集區

[!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)] 引進動態資料語言 (DDL) 以控制混合式緩衝集區。

下例針對 SQL Server 執行個體啟用混合式緩衝集區：

```sql
ALTER SERVER CONFIGURATION SET MEMORY_OPTIMIZED HYBRID_BUFFER_POOL = ON;
```

根據預設，混合式緩衝集區在執行個體的範圍設為停用。 請注意，為了讓設定變更生效，必須重新啟動 SQL Server 執行個體。 需要重新啟動以方便配置足夠的雜湊頁，納入伺服器的總 PMEM 容量。

下例針對特定資料庫啟用混合式緩衝集區。

```sql
ALTER DATABASE <databaseName> SET MEMORY_OPTIMIZED = ON;
```

根據預設，混合式緩衝集區在資料庫的範圍設為啟用。

## <a name="disable-hybrid-buffer-pool"></a>停用混合式緩衝集區

下例針對 SQL Server 執行個體停用混合式緩衝集區：

```sql
ALTER SERVER CONFIGURATION SET MEMORY_OPTIMIZED HYBRID_BUFFER_POOL = OFF;
```

根據預設，混合式緩衝集區在執行個體的範圍設為停用。 請注意，為了讓設定變更生效，必須重新啟動 SQL Server 執行個體。 需要重新啟動以防止過度配置雜湊頁，因為伺服器不需要計入 PMEM 容量。

下例針對特定資料庫停用混合式緩衝集區。

```sql
ALTER DATABASE <databaseName> SET MEMORY_OPTIMIZED = OFF;
```

根據預設，混合式緩衝集區在資料庫的範圍設為啟用。

## <a name="view-hybrid-buffer-pool-configuration"></a>檢視混合式緩衝集區設定

下例會傳回混合式緩衝集區系統設定之 SQL Server 執行個體的目前狀態。

```sql
SELECT *
FROM sys.configurations
WHERE
    name = 'hybrid_buffer_pool';
```

下例會傳回兩份資料表：

- 第一份顯示 SQL Server 執行個體的混合式緩衝集區系統設定目前狀態。
- 第二份列出混合式緩衝集區的資料庫和資料庫層級設定 (`is_memory_optimized_enabled`)。

```sql
SELECT * FROM sys.configurations WHERE name = 'hybrid_buffer_pool';

SELECT name, is_memory_optimized_enabled FROM sys.databases;
```

## <a name="best-practices-for-hybrid-buffer-pool"></a>混合式緩衝集區的最佳做法

小於 16-GB RAM 的執行個體，不建議啟用混合式緩衝集區。

在 Windows 上格式化 PMEM 裝置時，請使用 NTFS 可提供的最大配置單位大小 (Windows Server 2019 為 2 MB)，並確定裝置已針對 DAX (直接存取) 格式化。

檔案大小應該是 2 MB 的倍數 (模數 2 MB 應該等於零)。

如果混合式緩衝集區的伺服器範圍設定設為停用，則任何使用者資料庫都不使用混合式緩衝集區。

如果混合式緩衝集區的伺服器範圍設定設為啟用，您可以在這些使用者資料庫的資料庫範圍層級，遵循停用混合式緩衝集區的步驟，停用個別使用者資料庫的混合式緩衝集區使用。
