---
title: azdata arc dc endpoint 參考
titleSuffix: SQL Server big data clusters
description: azdata arc dc endpoint 命令的參考文章。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ea53bb8faef2534034a41422a83af1f16b81a5bf
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358806"
---
# <a name="azdata-arc-dc-endpoint"></a>azdata arc dc endpoint

適用於 [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

下列文章提供 **azdata** 工具中 **sql** 命令的參考。 如需其他 **azdata** 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)

## <a name="commands"></a>命令

|命令|描述|
| --- | --- |
[azdata arc dc endpoint list](#azdata-arc-dc-endpoint-list) | 列出資料控制器端點。
## <a name="azdata-arc-dc-endpoint-list"></a>azdata arc dc endpoint list
列出資料控制器端點。
```bash
azdata arc dc endpoint list [--endpoint-name -e] 
                            
```
### <a name="examples"></a>範例
列出特定命名空間中的資料控制器端點。
```bash
azdata arc dc endpoint list --namespace <ns>
```
### <a name="optional-parameters"></a>選擇性參數
#### `--endpoint-name -e`
Arc 資料控制器端點名稱。
### <a name="global-arguments"></a>全域引數
#### `--debug`
增加記錄詳細資訊，以顯示所有偵錯記錄。
#### `--help -h`
顯示此說明訊息並結束。
#### `--output -o`
輸出格式。  允許的值：json、jsonc、table、tsv。  預設值：json。
#### `--query -q`
JMESPath 查詢字串。 如需詳細資訊和範例，請參閱 [http://jmespath.org/](http://jmespath.org)。
#### `--verbose`
增加記錄詳細資訊。 使用 --debug 來取得完整偵錯記錄。

## <a name="next-steps"></a>後續步驟

如需其他 **azdata** 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)。 

如需如何安裝 **azdata** 工具的詳細資訊，請參閱[安裝 azdata](..\install\deploy-install-azdata.md)。

