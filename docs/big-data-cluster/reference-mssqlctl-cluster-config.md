---
title: mssqlctl 叢集組態參考
titleSuffix: SQL Server big data clusters
description: Mssqlctl 叢集命令的參考文件。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 57b77e83994f8471e677ba2ba367acc48a66cddd
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860019"
---
# <a name="mssqlctl-cluster-config"></a>mssqlctl cluster config

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

下列文章提供的參考**叢集組態**中的命令**mssqlctl**工具。 如需其他詳細資訊**mssqlctl**命令，請參閱[mssqlctl 參考](reference-mssqlctl.md)。

## <a id="commands"></a> 命令

|||
|---|---|
| [get](#get) | 取得叢集。 |

## <a id="get"></a> mssqlctl cluster config get

取得叢集。

```
mssqlctl cluster config get
   --name
   --output-file
```

### <a name="parameters"></a>參數

| 參數 | 描述 |
|---|---|
| **--name -n** | Kubernetes 命名空間所使用的叢集名稱。 必要。 |
| **--output-file -f** | 若要將結果儲存在輸出檔。 必要。 |

## <a name="next-steps"></a>後續步驟

如需其他詳細資訊**mssqlctl**命令，請參閱[mssqlctl 參考](reference-mssqlctl.md)。 如需有關如何安裝**mssqlctl**工具，請參閱[安裝來管理 SQL Server 2019 巨量資料叢集 mssqlctl](deploy-install-mssqlctl.md)。