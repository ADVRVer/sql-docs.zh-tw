---
title: mssqlctl 叢集參考
titleSuffix: SQL Server 2019 big data clusters
description: Mssqlctl 叢集命令的參考文件。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 130d3019d49deb7851696f6a1db2f77040734b31
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527211"
---
# <a name="mssqlctl-cluster"></a>mssqlctl 叢集

下列文章提供的參考**叢集**中的命令**mssqlctl**工具。 如需其他詳細資訊**mssqlctl**命令，請參閱[mssqlctl 參考](reference-mssqlctl.md)。

## <a id="commands"></a> 命令

|||
|---|---|
| [create](#create) | 建立叢集。 |
| [delete](#delete) | 刪除叢集。 |
| [config](reference-mssqlctl-cluster-config.md) | 叢集組態命令。 |
| [debug](reference-mssqlctl-cluster-debug.md) | 偵錯命令。 |

## <a id="create"></a> mssqlctl 叢集建立

建立叢集。

```
mssqlctl cluster create
   --name
   --accept-eula
```

### <a name="parameters"></a>參數

| 參數 | 描述 |
|---|---|
| **--name -n** | Kubernetes 命名空間所使用的叢集名稱。 |
| **--accept-eula -e** | 您接受授權條款嗎？ \[是/否\]。  允許的值： 否，[是]。 必要。 |

## <a id="delete"></a> mssqlctl cluster delete

刪除叢集。

```
mssqlctl cluster delete
   --name
   [--force]
```

### <a name="parameters"></a>參數

| 參數 | 描述 |
|---|---|
| **--name -n** | Kubernetes 命名空間所使用的叢集名稱。 必要。 |
| **--force -f** | 強制刪除叢集。 |

## <a name="next-steps"></a>後續步驟

如需其他詳細資訊**mssqlctl**命令，請參閱[mssqlctl 參考](reference-mssqlctl.md)。 如需有關如何安裝**mssqlctl**工具，請參閱[安裝來管理 SQL Server 2019 巨量資料叢集 mssqlctl](deploy-install-mssqlctl.md)。