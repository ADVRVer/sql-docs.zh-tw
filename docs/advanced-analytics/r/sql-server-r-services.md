---
title: 什麼是 SQL Server 2016 R Services？
titleSuffix: ''
description: R 服務是 SQL Server 2016 中的一項功能，可讓您使用關聯式資料來執行 R 指令碼。 您可以使用開放原始碼套件和架構及 Microsoft R 套件，來進行預測性分析和機器學習。 指令碼會在資料庫中執行，不需在 SQL Server 外部或透過網路來移動資料。 本文說明 SQL Server R Services 的基本概念。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/12/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 99aba9748e7ee6d53aabb18919324243740d996a
ms.sourcegitcommit: 1661c3e1bb38ed12f8485c3860fc2d2b97dd2c9d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71149927"
---
# <a name="what-is-sql-server-2016-r-services"></a>什麼是 SQL Server 2016 R Services？
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

R 服務是 SQL Server 2016 中的一項功能，可讓您使用關聯式資料來執行 R 指令碼。 您可以使用開放原始碼套件和架構及 [Microsoft R 套件](#packages)，來進行預測性分析和機器學習。 指令碼會在資料庫中執行，不需在 SQL Server 外部或透過網路來移動資料。 本文說明 SQL Server R Services 的基本概念。

> [!Note]
> 在 SQL Server 2017 和更新版本中，R 服務已重新命名為[機器學習服務](../what-is-sql-server-machine-learning.md)，並且同時支援 Python 與 R。

## <a name="what-is-r-services"></a>什麼是 R 服務？

SQL Server R Services 可讓您在資料庫內執行 R 指令碼。 您可以使用它來準備和清除資料、進行特徵工程和定型、評估，以及在資料庫內部署機器學習模型。 此功能可讓您在資料所在的位置執行程式碼，而無須透過網路將資料傳輸至另一部伺服器。

R 服務中包含基礎 R 散發。 除了 Microsoft R 套件 [RevoScaleR](../r/ref-r-revoscaler.md)、[MicrosoftML](../r/ref-r-microsoftml.md)、[olapR]../r/ref-r-olapr.md) 及適用於 R 的 [sqlrutils](../r/ref-r-sqlrutils.md) 之外，您還可以使用開放原始碼套件和架構。

R 服務使用擴充性架構在 SQL Server 中執行 R 指令碼。 深入了解運作方式：

+ [擴充性架構](../concepts/extensibility-framework.md)
+ [R 延伸模組](../concepts/extension-r.md)

## <a name="what-can-i-do-with-r-services"></a>我可以使用 R 服務來做什麼？

您可以使用 R 服務在 SQL Server 內建置機器學習和深度學習模型，並將這些模型定型。 您也可以將現有模型部署至 R 服務，並使用關聯式資料來進行預測。

您可以使用 SQL Server R Services 來進行的預測類型範例包括：

|||
|-|-|
|分類|自動將客戶意見反應分成正面和負面類別|
|迴歸/預測連續數值|根據大小和位置來預測房屋價格|
|異常偵測|偵測詐騙銀行交易 |
|建議|根據線上顧客先前的購買來建議他們可能想要購買的產品|

### <a name="how-to-execute-r-scripts"></a>如何執行 R 指令碼

有兩種執行 R 服務中 R 指令碼的方式：

+ 最常見的方式是使用 T-SQL 預存程序 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)。

+ 您也可以使用慣用的 R 用戶端，然後撰寫會將執行 (稱為「遠端計算內容」  ) 推送至遠端 SQL Server 的指令碼。 如需詳細資訊，請參閱[設定資料科學用戶端 R 開發](../r/set-up-a-data-science-client.md)。

<a name="packages"></a>

## <a name="r-packages"></a>R 套件

除了 Microsoft 的企業套件之外，您還可以使用開放原始碼套件和架構。 R 服務中已預先安裝最常見的開放原始碼 R 套件。 此外，也包含下列來自 Microsoft 的 R 套件：

| 封裝 | Description |
|-|-|
| [RevoScaleR](../r/ref-r-revoscaler.md) | 可調整 R 的主要套件。資料轉換與操作、統計摘要、視覺化，以及許多模型化形式。 此外，此套件中的函式會自動在可用的核心之間分配工作負載來進行平行處理。 |
| [MicrosoftML (R)](../r/ref-r-microsoftml.md) | 新增機器學習演算法來建立自訂模型，以進行文字分析、影像分析及情感分析。 |
| [olapR](../r/ref-r-olapr.md) | 用於針對 SQL Server Analysis Services OLAP cube 執行 MDX 查詢的 R 函式。 |
| [sqlrutils](../r/ref-r-sqlrutils.md) | 一種機制，可在 T-SQL 預存程序中使用 R 指令碼、向資料庫註冊該預存程序，然後從 [R 開發環境](../r/set-up-a-data-science-client.md)中執行該預存程序。 |
| [Microsoft R Open](https://mran.microsoft.com/rro) | Microsoft R Open (MRO) 是 Microsoft 所提供的增強 R 散發。 這是一個適用於統計分析與資料科學的完整開放原始碼平台。 它以 R 為基礎並與其 100% 相容，且包含可提升效能和重現性的額外功能。 |

## <a name="how-do-i-get-started-with-rservices"></a>如何開始使用 RServices？

1. [安裝 SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

1. 設定開發工具。 您可以使用：

    + [Azure Data Studio](../../azure-data-studio/what-is.md) 或 [SQL Server Management Studio (SSMS)](../../ssms/sql-server-management-studio-ssms.md) 以使用 T-SQL 和預存程序 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 來執行您的 R 指令碼。
    + 您自己的開發筆記型電腦或工作站上的 R 來執行指令碼。 您可以使用 [RevoScaleR](../r/ref-r-revoscaler.md)將資料提取至本機或將執行推送到遠端給 SQL Server。 如需詳細資訊，請參閱[設定資料科學用戶端 R 開發](../r/set-up-a-data-science-client.md)。

1. 撰寫您的第一個 R 指令碼

    + 快速入門：[在 SQL Server 中建立和執行簡單的 R 指令碼](../tutorials/quickstart-r-create-script.md)
    + 快速入門：[在 R 中建立預測模型並將其定型](../tutorials/quickstart-r-train-score-model.md)
    + 教學課程：[在 T-SQL 中使用 R](../tutorials/sqldev-in-database-r-for-sql-developers.md)：探索資料、執行特徵工程、將模型定型並部署，以及進行預測 (五部分系列)
    + 教學課程：[在 R 工具中使用 R 服務](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)：探索資料、建立圖表和繪圖、執行特徵工程、將模型定型並部署，以及進行預測 (六部分系列)

## <a name="next-steps"></a>後續步驟

+ [安裝 SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [設定用於 R 開發的資料科學用戶端](../r/set-up-a-data-science-client.md)