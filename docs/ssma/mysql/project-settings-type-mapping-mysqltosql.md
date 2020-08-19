---
description: 專案設定 (類型對應) (MySQLToSQL)
title: 專案設定 (類型對應)  (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: a6f4bc99caceeb7011c932c86e636304941c459c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418484"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>專案設定 (類型對應) (MySQLToSQL)
型別對應專案設定可讓您設定 SSMA 專案的預設型別對應。  

[專案設定] 和 [預設專案設定] 對話方塊中有提供類型對應：  
  
-   使用 [專案設定] 對話方塊，即可設定目前專案的設定選項。 若要存取型別對應設定，請在 [工具] 功能表上選取 [專案設定]，然後按一下左窗格中的 [類型對應]。  
  
-   使用 [預設專案設定] 對話方塊，即可設定所有專案的設定選項。 若要存取型別對應設定，請在 [工具] 功能表上，選取 [預設專案設定]，選取 [/changed 從 **遷移目標版本** ] 下拉式清單中需要觀看設定的 [遷移專案類型]，然後按一下左窗格中的 [類型對應]。  
  
## <a name="options"></a>選項。  
  
##### <a name="source-type"></a>來源類型  
這是 MySQL 資料類型，必須對應至目標資料庫資料類型。  
  
##### <a name="target-type"></a>目標類型  
指定之 MySQL 資料類型的目標資料庫資料類型。  
  
##### <a name="add"></a>新增  
按一下以將資料類型加入至對應清單。  
  
##### <a name="edit"></a>編輯  
按一下即可編輯 [對應] 清單中所選取的資料類型。  
  
##### <a name="remove"></a>移除  
按一下即可從 [對應] 清單中移除選取的資料類型對應。  
  
##### <a name="reset-to-default"></a>重設為預設值  
按一下以將類型對應清單重設為 SSMA 預設值。  
  
## <a name="type-mappings"></a>型別對應  
下表顯示來源與目標資料類型之間的預設對應。  
  
|MySQL 資料類型|SQL Server 資料類型|  
|-|-|  
|BIGINT|BIGINT|  
|Bigint [* .。。255]|BIGINT|  
|BINARY|二進位檔 [1]|  
|binary [0 ..1]|二進位檔 [1]|  
|二進位 [2. 255]|binary [*]|  
|bit|二進位檔 [1]|  
|位 [0 ... 8]|二進位檔 [1]|  
|位 [17.. 24]|二進位 [3]|  
|位 [25.. 32]|二進位 [4]|  
|位 [33. 40]|二進位 [5]|  
|位 [41. 48]|二進位 [6]|  
|位 [49. 56]|二進位 [7]|  
|位 [57.. 64]|二進位 [8]|  
|位 [9.. 16]|二進位 [2]|  
|blob|varbinary(max)|  
|blob [0 ..1]|Varbinary [1]|  
|blob [2. 8000]|Varbinary [*]|  
|blob [8001 ... *]|varbinary(max)|  
|bool|bit|  
|boolean|bit|  
|char|Nchar [1]|  
|char 位元組|二進位檔 [1]|  
|char byte [0 ..1]|二進位檔 [1]|  
|char byte [2 ... 255]|binary [*]|  
|char [0 ..1]|Nchar [1]|  
|char [2 ... 255]|Nchar [*]|  
|character|Nchar [1]|  
|字元差異 [0 ..1]|Nvarchar [1]|  
|字元差異 [2. 255]|NVARCHAR|  
|字元 [0 ..1]|Nchar [1]|  
|字元 [2 ... 255]|Nchar [*]|  
|date|date|  
|Datetime|datetime2 [0]|  
|dec|decimal|  
|dec [*.。65]|decimal [*] [0]|  
|dec [*.。65] [ \* .。。30|decimal [*] [ \* ]|  
|decimal|decimal|  
|decimal [*.。65]|decimal [*] [0]|  
|decimal [*.。65] [ \* .。。30|decimal [*] [ \* ]|  
|double|float [53]|  
|雙精度|float [53]|  
|雙精確度 [* .。。255] [ \* .。。30|數值 [*] [ \* ]|  
|double [* .。。255] [ \* .。。30|數值 [*] [ \* ]|  
|fixed|NUMERIC|  
|fixed [* .。。65] [ \* .。。30|數值 [*] [ \* ]|  
|FLOAT|float [24]|  
|float [* .。。255] [ \* .。。30|數值 [*] [ \* ]|  
|float [* .。。53]|float [53]|  
|int|int|  
|int [* .。。255]|int|  
|integer|int|  
|整數 [* .。。255]|int|  
|longblob|varbinary(max)|  
|longtext|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|int|  
|mediumint[*..255]|int|  
|mediumtext|nvarchar(max)|  
|國家/地區字元|Nchar [1]|  
|國家字元 [0 ..1]|Nchar [1]|  
|國家字元 [2. 255]|Nchar [*]|  
|國家字元|Nchar [1]|  
|國家字元變動|Nvarchar [1]|  
|國際字元不同 [0 ..1]|Nvarchar [1]|  
|國際字元不同 [2. 4000]|Nvarchar [*]|  
|國際字元不同 [4001.. *]|nvarchar(max)|  
|國家字元 [0 ..1]|Nchar [1]|  
|國家字元 [2.. 255]|Nchar [*]|  
|全國 Varchar|Nvarchar [1]|  
|全國 Varchar [0 ..1]|Nvarchar [1]|  
|全國 Varchar [2. 4000]|Nvarchar [*]|  
|全國 Varchar [4001.. *]|nvarchar(max)|  
|NCHAR|Nchar [1]|  
|Nchar Varchar|Nvarchar [1]|  
|Nchar Varchar [0 ..1]|Nvarchar [1]|  
|Nchar Varchar [2. 4000]|Nvarchar [*]|  
|Nchar Varchar [4001. *]|nvarchar(max)|  
|Nchar [0 ..1]|Nchar [1]|  
|Nchar [2. 255]|Nchar [*]|  
|NUMERIC|NUMERIC|  
|數值 [* .。。65]|數值 [*] [0]|  
|數值 [* .。。65] [ \* .。。30|數值 [*] [ \* ]|  
|NVARCHAR|Nvarchar [1]|  
|Nvarchar [0 ..1]|Nvarchar [1]|  
|Nvarchar [2. 4000]|Nvarchar [*]|  
|Nvarchar [4001.. *]|nvarchar(max)|  
|real|float [53]|  
|real [* .。。255] [ \* .。。30|數值 [*] [ \* ]|  
|serial|BIGINT|  
|SMALLINT|SMALLINT|  
|Smallint [* .。。255]|SMALLINT|  
|text|nvarchar(max)|  
|文字 [0 ..1]|Nvarchar [1]|  
|文字 [2.. 4000]|Nvarchar [*]|  
|文字 [4001.. *]|nvarchar(max)|  
|time|time|  
|timestamp|Datetime|  
|tinyblob|Varbinary [255]|  
|TINYINT|SMALLINT|  
|Tinyint [* .。。255]|SMALLINT|  
|tinytext|Nvarchar [255]|  
|不帶正負號的 Bigint|BIGINT|  
|未簽署的 Bigint [* .。。255]|BIGINT|  
|不帶正負號的 dec|decimal|  
|未簽署的 dec [*.。65]|decimal [*] [0]|  
|未簽署的 dec [*.。65] [ \* .。。30|decimal [*] [ \* ]|  
|不帶正負號的十進位|decimal|  
|不帶正負號的 decimal [*.。65]|decimal [*] [0]|  
|不帶正負號的 decimal [*.。65] [ \* .。。30|decimal [*] [ \* ]|  
|無符號雙精度浮點數|float [53]|  
|不帶正負號的雙精確度|float [53]|  
|不帶正負號的雙精確度 [*.。255] [ \* .。。30|數值 [*] [ \* ]|  
|不帶正負號的雙重 [* .。。255] [ \* .。。30|數值 [*] [ \* ]|  
|未簽署的固定|NUMERIC|  
|未簽署的固定 [* .。。65] [ \* .。。30|數值 [*] [ \* ]|  
|不帶正負號的 float|float [24]|  
|不帶正負號的 float [* .。。255] [ \* .。。30|數值 [*] [ \* ]|  
|不帶正負號的 float [* .。。53]|float [53]|  
|不帶正負號的整數|BIGINT|  
|不帶正負號的 int [* .。。255]|BIGINT|  
|不帶正負號的整數|BIGINT|  
|不帶正負號的整數 [*.。255]|BIGINT|  
|未簽署的 mediumint|int|  
|未簽署的 mediumint [* .。。255]|int|  
|不帶正負號的數值|NUMERIC|  
|不帶正負號的數值 [* .。。65]|數值 [*] [0]|  
|不帶正負號的數值 [* .。。65] [ \* .。。30|數值 [*] [ \* ]|  
|不帶正負號的真實|float [53]|  
|不帶正負號的實際 [* .。。255 [[ \* .。。30|數值 [*] [ \* ]|  
|不帶正負號的 Smallint|int|  
|不帶正負號的 Smallint [* .。。255]|int|  
|不帶正負號的 Tinyint|TINYINT|  
|不帶正負號的 Tinyint [* .。。255]|TINYINT|  
|Varbinary [0 ..1]|Varbinary [1]|  
|Varbinary [2. 8000]|Varbinary [*]|  
|Varbinary [8001 ... *]|varbinary(max)|  
|Varchar [0 ..1]|Nvarchar [1]|  
|Varchar [2. 4000]|Nvarchar [*]|  
|Varchar [4001.. *]|nvarchar(max)|  
|year|SMALLINT|  
|year [2.. 2]|SMALLINT|  
|year [4. 4. 4]|SMALLINT|  
  
##### <a name="add"></a>新增  
按一下以將資料類型加入至對應清單。  
  
##### <a name="edit"></a>編輯  
按一下即可編輯 [對應] 清單中的資料類型。  
  
##### <a name="remove"></a>移除  
按一下即可從 [對應] 清單中移除選取的資料類型對應。  
  
##### <a name="reset-to-default"></a>重設為預設值  
按一下以將所有資料類型對應重設為 SSMA 預設值。  
  
