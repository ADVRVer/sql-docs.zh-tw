---
title: 在 SQL Server 機器學習中的 Python 程式庫和資料類型 |Microsoft 文件
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f8dfa7f343a3a179b05b624a083238e08011c4a5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201690"
---
# <a name="python-libraries-and-data-types"></a>Python 程式庫和資料類型
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

本文說明隨附於 SQL Server 機器學習服務 （資料庫） 和 （獨立） 安裝的 Python 程式庫。

本文也會列出不支援的資料類型和清單的資料類型轉換的 Python 和 SQL Server 之間傳遞資料時可能會隱含地執行。

## <a name="python-version"></a>Python 版本

SQL Server 2017 CTP 2.0 包含 Anaconda 發佈和 Python 3.6 的一部分。

RevoScaleR 功能子集 (rxLinMod，rxLogit，rxPredict，rxDTrees，rxBTrees，可能只有幾個其他項目) 會使用的 Api Python，使用新的 Python 封裝提供**revoscalepy**。 您可以使用此套件使用熊資料框架、 XDF 檔案或 SQL 資料查詢的資料。

如需詳細資訊，請參閱[何謂 revoscalepy？](what-is-revoscalepy.md)。

## <a name="python-and-sql-data-types"></a>Python 和 SQL 資料類型

Python 支援有限的數目的資料類型，相較於 SQL Server。

如此一來，每當您使用的資料[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Python 指令碼中的資料可能會隱含地轉換成相容的資料類型。 不過，通常完全無法執行轉換，而且會傳回錯誤。

下表列出所提供的隱含轉換。 不支援其他資料型別。

|SQLtype|Python 類型|
|-|-|
|**bigint**|`numeric`|
|**binary**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float32`|
|**smallint**|`int16`|
|**tinyint**|`uint8`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|



