---
title: azdata bdc spark statement 參考
titleSuffix: SQL Server big data clusters
description: azdata bdc spark statement 命令的參考文章。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 272a633a347f767145476e770e2d9b64b7470e49
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153084"
---
# <a name="azdata-bdc-spark-statement"></a>azdata bdc spark statement

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

本文是**azdata**的參考文章。 

## <a name="commands"></a>命令
|     |     |
| --- | --- |
[azdata bdc spark statement list](#azdata-bdc-spark-statement-list) | 列出指定 Spark 工作階段中的所有陳述式。
[azdata bdc spark statement create](#azdata-bdc-spark-statement-create) | 在指定的工作階段中建立一個新的 Spark 陳述式。
[azdata bdc spark statement info](#azdata-bdc-spark-statement-info) | 取得指定 Spark 工作階段中所要求陳述式的相關資訊。
[azdata bdc spark statement cancel](#azdata-bdc-spark-statement-cancel) | 取消指定 Spark 工作階段中的陳述式。
## <a name="azdata-bdc-spark-statement-list"></a>azdata bdc spark statement list
列出指定 Spark 工作階段中的所有陳述式。
```bash
azdata bdc spark statement list --session-id -i 
                                
```
### <a name="examples"></a>範例
列出所有的工作階段陳述式。
```bash
azdata spark statement list --session-id 0
```
### <a name="required-parameters"></a>必要參數
#### `--session-id -i`
Spark 工作階段識別碼。
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
## <a name="azdata-bdc-spark-statement-create"></a>azdata bdc spark statement create
This creates and executes a new statement in the given session.  如果執行速度很快，則結果會包含執行的輸出。  否則，在陳述式完成後，可以使用 'spark session info' 來取出結果。
```bash
azdata bdc spark statement create --session-id -i 
                                  --code -c
```
### <a name="examples"></a>範例
執行陳述式。
```bash
azdata spark statement create --session-id 0 --code "2+2"
```
### <a name="required-parameters"></a>必要參數
#### `--session-id -i`
Spark 工作階段識別碼。
#### `--code -c`
字串，包含要當做陳述式一部分執行的程式碼。
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
## <a name="azdata-bdc-spark-statement-info"></a>azdata bdc spark statement info
如果陳述式已完成，則取得執行狀態和執行結果。 陳述式識別碼會從 'spark statement create' 傳回。
```bash
azdata bdc spark statement info --session-id -i 
                                --statement-id -s
```
### <a name="examples"></a>範例
取得識別碼為 0 且陳述式識別碼為 0 的工作階段的陳述式資訊。
```bash
azdata spark statement info --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>必要參數
#### `--session-id -i`
Spark 工作階段識別碼。
#### `--statement-id -s`
指定工作階段識別碼中的 Spark 陳述式識別碼。
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
## <a name="azdata-bdc-spark-statement-cancel"></a>azdata bdc spark statement cancel
這會取消指定 Spark 工作階段中的陳述式。 陳述式識別碼會從 'spark statement create' 傳回。
```bash
azdata bdc spark statement cancel --session-id -i 
                                  --statement-id -s
```
### <a name="examples"></a>範例
取消陳述式。
```bash
azdata spark statement cancel --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>必要參數
#### `--session-id -i`
Spark 工作階段識別碼。
#### `--statement-id -s`
指定工作階段識別碼中的 Spark 陳述式識別碼。
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
