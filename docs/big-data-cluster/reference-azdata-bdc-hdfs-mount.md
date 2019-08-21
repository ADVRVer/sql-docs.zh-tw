---
title: azdata bdc hdfs mount reference
titleSuffix: SQL Server big data clusters
description: azdata bdc hdfs mount 命令的參考文章。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: eca0bf6cab7d88d91bc52daf88d5e71cf652d474
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653696"
---
# <a name="azdata-bdc-hdfs-mount"></a>azdata bdc hdfs mount

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

下列文章提供 **azdata** 工具中 **bdc hdfs mount** 命令的參考。 如需其他 **azdata** 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)。

## <a name="commands"></a>命令
|     |     |
| --- | --- |
[azdata bdc hdfs mount create](#azdata-bdc-hdfs-mount-create) | 建立 HDFS 中遠端存放庫的裝載。
[azdata bdc hdfs mount delete](#azdata-bdc-hdfs-mount-delete) | 刪除 HDFS 中遠端存放庫的裝載。
[azdata bdc hdfs mount status](#azdata-bdc-hdfs-mount-status) | 裝載的狀態。
[azdata bdc hdfs mount refresh](#azdata-bdc-hdfs-mount-refresh) | 重新整理 HDFS 中裝載的內容。
## <a name="azdata-bdc-hdfs-mount-create"></a>azdata bdc hdfs mount create
建立 HDFS 中遠端存放庫的裝載。 用來存取遠端存放庫的認證 (若有的話) 應該要使用環境變數 MOUNT_CREDENTIALS 作為 key=value 組的逗點分隔清單來加以指定。 必須逸出金鑰或值中的所有逗點。
```bash
azdata bdc hdfs mount create --remote-uri -r 
                             --mount-path -m
```
### <a name="examples"></a>範例
若要使用共用金鑰將 "data" 容器裝載在 HDFS 路徑 /mounts/adlsv2/data 上的 ADLS Gen 2 帳戶 "adlsv2example" 中
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
azdata bdc hdfs mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
若要在本機 HDFS 路徑 /mounts/hdfs/ 上裝載遠端 HDFS BDC (hdfs://namenode1:8080/)
```bash
azdata bdc hdfs mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>必要參數
#### `--remote-uri -r`
要裝載之遠端存放庫的 URI (裝載的來源)。
#### `--mount-path -m`
必須建立裝載的 HDFS 路徑 (裝載的目的地)。
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
## <a name="azdata-bdc-hdfs-mount-delete"></a>azdata bdc hdfs mount delete
刪除 HDFS 中遠端存放庫的裝載。
```bash
azdata bdc hdfs mount delete --mount-path -m 
                             
```
### <a name="examples"></a>範例
刪除在 /mounts/adlsv2/data 針對 ADLS Gen 2 儲存體帳戶所建立的裝載。
```bash
azdata bdc hdfs mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>必要參數
#### `--mount-path -m`
必須刪除對應至裝載的 HDFS 路徑。
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
## <a name="azdata-bdc-hdfs-mount-status"></a>azdata bdc hdfs mount status
裝載的狀態。
```bash
azdata bdc hdfs mount status [--mount-path -m] 
                             
```
### <a name="examples"></a>範例
依路徑取得裝載狀態
```bash
azdata bdc hdfs mount status --mount-path /mounts/hdfs
```
取得所有裝載的狀態。
```bash
azdata bdc hdfs mount status
```
### <a name="optional-parameters"></a>選擇性參數
#### `--mount-path -m`
裝載路徑。
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
## <a name="azdata-bdc-hdfs-mount-refresh"></a>azdata bdc hdfs mount refresh
重新整理 HDFS 中裝載的內容。
```bash
azdata bdc hdfs mount refresh --mount-path -m 
                              
```
### <a name="examples"></a>範例
重新整理在 /mounts/adlsv2/data 建立的裝載。
```bash
azdata bdc hdfs mount refresh --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>必要參數
#### `--mount-path -m`
必須重新整理對應至裝載的 HDFS 路徑。
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

如需其他 **azdata** 命令的詳細資訊，請參閱 [azdata 參考](reference-azdata.md)。 如需有關如何安裝**azdata**工具的詳細資訊, 請參閱[install azdata to [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]manage ](deploy-install-azdata.md)。
