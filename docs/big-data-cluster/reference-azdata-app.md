---
title: azdata app 參考
titleSuffix: SQL Server big data clusters
description: azdata app 命令的參考文章。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7cb67f55af03fc8c948df6f17ee2924dea12825f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "74820976"
---
# <a name="azdata-app"></a>azdata app

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

下文提供 `azdata` 工具中 `app` 命令的參考。 如需其他 `azdata` 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)

## <a name="commands"></a>命令
|     |     |
| --- | --- |
[azdata app template](reference-azdata-app-template.md) | 範本。
[azdata app init](#azdata-app-init) | 快速啟動新的應用程式基本架構。
[azdata app create](#azdata-app-create) | 建立應用程式。
[azdata app update](#azdata-app-update) | 更新應用程式。
[azdata app list](#azdata-app-list) | 列出應用程式。
[azdata app delete](#azdata-app-delete) | 刪除應用程式。
[azdata app run](#azdata-app-run) | 執行應用程式。
[azdata app describe](#azdata-app-describe) | 描述應用程式。
## <a name="azdata-app-init"></a>azdata app init
協助您根據執行階段環境啟動新的應用程式基本架構和/或規格檔案。
```bash
azdata app init [--spec -s] 
                [--name -n]  
                [--version -v]  
                [--template -t]  
                [--destination -d]  
                [--url -u]
```
### <a name="examples"></a>範例
僅建立新的 `spec.yaml` 應用程式。
```bash
azdata app init --spec
```
根據 `r` 範本，建立新的 R 應用程式基本架構。
```bash
azdata app init --name reduce --template r
```
根據 `python` 範本，建立新的 Python 應用程式基本架構。
```bash
azdata app init --name reduce --template python
```
根據 `ssis` 範本，建立新的 SSIS 應用程式基本架構。
```bash
azdata app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>選擇性參數
#### `--spec -s`
僅產生應用程式 spec.yaml。
#### `--name -n`
應用程式名稱。
#### `--version -v`
應用程式版本。
#### `--template -t`
範本名稱。 如需支援的範本名稱完整清單，請執行 `azdata app template list`
#### `--destination -d`
應用程式基本架構的放置位置。 預設：目前的工作目錄。
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
## <a name="azdata-app-create"></a>azdata app create
建立應用程式。
```bash
azdata app create --spec -s 
```
### <a name="examples"></a>範例
從包含有效 spec.yaml 部署規格的目錄建立新的應用程式。
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>必要參數
#### `--spec -s`
目錄路徑，其中包含描述應用程式的 YAML 規格檔案。
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
## <a name="azdata-app-update"></a>azdata app update
更新應用程式。
```bash
azdata app update [--spec -s] 
                  [--yes -y]
```
### <a name="examples"></a>範例
從包含有效 spec.yaml 部署規格的目錄更新現有的應用程式。
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>選擇性參數
#### `--spec -s`
目錄路徑，其中包含描述應用程式的 YAML 規格檔案。
#### `--yes -y`
從 CWD 的 spec.yaml 檔案更新應用程式時，不要提示確認。
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
## <a name="azdata-app-list"></a>azdata app list
列出應用程式。
```bash
azdata app list [--name -n] 
                [--version -v]
```
### <a name="examples"></a>範例
依名稱和版本列出應用程式。
```bash
azdata app list --name reduce  --version v1
```
依名稱列出所有應用程式版本。
```bash
azdata app list --name reduce
```
依名稱列出所有應用程式版本。
```bash
azdata app list
```
### <a name="optional-parameters"></a>選擇性參數
#### `--name -n`
應用程式名稱。
#### `--version -v`
應用程式版本。
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
## <a name="azdata-app-delete"></a>azdata app delete
刪除應用程式。
```bash
azdata app delete --name -n 
                  --version -v
```
### <a name="examples"></a>範例
依名稱和版本刪除應用程式。
```bash
azdata app delete --name reduce --version v1    
```
### <a name="required-parameters"></a>必要參數
#### `--name -n`
應用程式名稱。
#### `--version -v`
應用程式版本。
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
## <a name="azdata-app-run"></a>azdata app run
執行應用程式。
```bash
azdata app run --name -n 
               --version -v  
               [--inputs]
```
### <a name="examples"></a>範例
執行沒有輸入參數的應用程式。
```bash
azdata app run --name reduce --version v1
```
執行具有 1 個輸入參數的應用程式。
```bash
azdata app run --name reduce --version v1 --inputs x=10
```
執行具有多個輸入參數的應用程式。
```bash
azdata app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>必要參數
#### `--name -n`
應用程式名稱。
#### `--version -v`
應用程式版本。
### <a name="optional-parameters"></a>選擇性參數
#### `--inputs`
CSV `name=value` 格式的應用程式輸入參數。
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
## <a name="azdata-app-describe"></a>azdata app describe
描述應用程式。
```bash
azdata app describe [--spec -s] 
                    [--name -n]  
                    [--version -v]
```
### <a name="examples"></a>範例
描述應用程式。
```bash
azdata app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>選擇性參數
#### `--spec -s`
目錄路徑，其中包含描述應用程式的 YAML 規格檔案。
#### `--name -n`
應用程式名稱。
#### `--version -v`
應用程式版本。
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
