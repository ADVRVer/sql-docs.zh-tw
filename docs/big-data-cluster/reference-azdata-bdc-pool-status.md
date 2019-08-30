---
title: azdata bdc pool status 參考
titleSuffix: SQL Server big data clusters
description: azdata bdc pool status 命令的參考文章。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ee49ee09107c98047bd5aea849b9ae486eb6736a
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153117"
---
# <a name="azdata-bdc-pool-status"></a>azdata bdc pool status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

本文是**azdata**的參考文章。 

## <a name="commands"></a>命令
|     |     |
| --- | --- |
[azdata bdc pool status show](#azdata-bdc-pool-status-show) | 集區狀態。
## <a name="azdata-bdc-pool-status-show"></a>azdata bdc pool status show
集區狀態。
```bash
azdata bdc pool status show --kind -k 
                            [--name -n]
```
### <a name="examples"></a>範例
取得存放集區的狀態。
```bash
azdata bdc pool status show --kind storage --name default
```
取得資料集區的狀態。
```bash
azdata bdc pool status show --kind data --name default
```
取得計算集區的狀態。
```bash
azdata bdc pool status show --kind compute --name default
```
取得主要集區的狀態。
```bash
azdata bdc pool status show --kind master --name default
```
取得 spark 集區的狀態。
```bash
azdata bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>必要參數
#### `--kind -k`
巨量資料叢集集區種類。
### <a name="optional-parameters"></a>選擇性參數
#### `--name -n`
巨量資料叢集集區名稱。
`default`
### <a name="global-arguments"></a>全域引數
#### `--debug`
增加記錄詳細資訊，以顯示所有偵錯記錄。
#### `--help -h`
顯示此說明訊息並結束。
#### `--output -o`
輸出格式。  允許的值：json、jsonc、table、tsv。  預設值：json。
#### `--query -q`
JMESPath 查詢字串。 如需詳細資訊和範例，請參閱 [http://jmespath.org/](http://jmespath.org/])。
#### `--verbose`
增加記錄詳細資訊。 使用 --debug 來取得完整偵錯記錄。

## <a name="next-steps"></a>後續步驟

- 如需其他 **azdata** 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)。 

- 如需如何安裝 **azdata** 工具的詳細資訊，請參閱[安裝 azdata 來管理 SQL Server 2019 巨量資料叢集](deploy-install-azdata.md)。
