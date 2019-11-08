---
title: azdata app template reference
titleSuffix: SQL Server big data clusters
description: azdata app template 命令的參考文章。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3cdee262be7ef0c14d935c95eb9389d4a3ae03a3
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531917"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

下列文章提供 `azdata` 工具中 `sql` 命令的參考。 如需其他 `azdata` 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)

## <a name="commands"></a>命令
|     |     |
| --- | --- |
[`azdata app template list`](#azdata-app-template-list) | 擷取支援的範本。
[`azdata app template pull`](#azdata-app-template-pull) | 下載支援的範本。
## <a name="azdata-app-template-list"></a>azdata app template list
在指定的 [URL] GitHub 存放庫底下擷取支援的範本。
```bash
azdata app template list [--url -u]
```
### <a name="examples"></a>範例
在預設的範本存放庫位置底下擷取所有範本。
```bash
azdata app template list
```
在不同的存放庫位置底下擷取所有範本。
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>選擇性參數
#### `--url -u`
指定不同的範本存放庫位置。 預設： https://github.com/Microsoft/SQLBDC-AppDeploy.git
### <a name="global-arguments"></a>全域引數
#### `--debug`
增加記錄詳細資訊，以顯示所有偵錯記錄。
#### `--help -h`
顯示此說明訊息並結束。
#### `--output -o`
輸出格式。  允許的值：json、jsonc、table、tsv。  預設值：json。
#### `--query -q`
JMESPath 查詢字串。 如需詳細資訊和範例，請參閱 [http://jmespath.org/](http://jmespath.org/)。
#### `--verbose`
增加記錄詳細資訊。 使用 --debug 來取得完整偵錯記錄。
## <a name="azdata-app-template-pull"></a>azdata app template pull
在指定的 [URL] GitHub 存放庫底下下載支援的範本。
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         [--destination -d]
```
### <a name="examples"></a>範例
在預設的範本存放庫位置底下下載所有範本。
```bash
azdata app template pull
```
在不同的存放庫位置底下下載所有範本。
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
依名稱個別下載範本。
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>選擇性參數
#### `--name -n`
範本名稱。 如需支援的範本名稱完整清單，請執行 `azdata app template list`
#### `--url -u`
指定不同的範本存放庫位置。 預設： https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
應用程式基本架構範本的放置位置。
`./templates`
### <a name="global-arguments"></a>全域引數
#### `--debug`
增加記錄詳細資訊，以顯示所有偵錯記錄。
#### `--help -h`
顯示此說明訊息並結束。
#### `--output -o`
輸出格式。  允許的值：json、jsonc、table、tsv。  預設值：json。
#### `--query -q`
JMESPath 查詢字串。 如需詳細資訊和範例，請參閱 [http://jmespath.org/](http://jmespath.org/)。
#### `--verbose`
增加記錄詳細資訊。 使用 --debug 來取得完整偵錯記錄。

## <a name="next-steps"></a>後續步驟

如需其他 `azdata` 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)。 如需如何安裝 `azdata` 工具的詳細資訊，請參閱[安裝 azdata 來管理 SQL Server 2019 巨量資料叢集](deploy-install-azdata.md)。
