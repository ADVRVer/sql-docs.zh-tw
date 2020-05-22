---
title: 快速入門：Python 函式
description: 在此快速入門中，您將會了解如何搭配 SQL Server 機器學習服務使用 Python 數學與公用程式函式。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/28/2020
ms.topic: quickstart
author: cawrites
ms.author: chadam
ms.reviewer: garye
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6afe1685956c43e30ace59f3e5cc794a2abbd88f
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606701"
---
# <a name="quickstart-python-functions-with-sql-server-machine-learning-services"></a>快速入門：Python 函式搭配 SQL Server 機器學習服務
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
在此快速入門中，您將會了解如何搭配 [SQL Server 機器學習服務](../sql-server-machine-learning-services.md)或[巨量資料叢集](../../big-data-cluster/machine-learning-services.md)使用 Python 數學與公用程式函式。 使用 T-SQL 實作統計函數通常會很複雜，但若使用 Python，只需要幾行程式碼就可以完成。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
在此快速入門中，您將會了解如何搭配 [SQL Server 機器學習服務](../sql-server-machine-learning-services.md)使用 Python 數學與公用程式函式。 使用 T-SQL 實作統計函數通常會很複雜，但若使用 Python，只需要幾行程式碼就可以完成。
::: moniker-end

## <a name="prerequisites"></a>Prerequisites

- 本快速入門需使用已安裝 Python 語言的 [SQL Server 機器學習服務](../install/sql-machine-learning-services-windows-install.md)來存取 SQL Server 的執行個體。

  您的 SQL Server 執行個體可以位於 Azure 虛擬機器或內部部署中。 請注意，外部指令碼功能預設為停用，因此可能需要[啟用外部指令碼](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature)，並在開始之前確認 **SQL Server Launchpad 服務**正在執行。

- 您也需要工具來執行包含 Python 指令碼的 SQL 查詢。 您可以使用任何資料庫管理或查詢工具來執行這些指令碼，只要該工具可以連線到 SQL Server 執行個體，並執行 T-SQL 查詢或預存程序即可。 本快速入門使用 [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download-azure-data-studio)。

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>建立預存程序來產生亂數

為了方便作業，讓我們使用 Python `numpy` 套件；此套件會預設安裝及載入到已安裝 Python 的 SQL Server 機器學習服務。 該套件包含數百個用來進行一般統計工作的函式，其中 `random.normal` 函式會在指定標準差和平均值的情況下，使用常態分佈產生指定數目的亂數。

例如，下列 Python 程式碼會在指定標準差為 3 的情況下，傳回平均值為 50 的 100 個數字。

```Python
numpy.random.normal(size=100, loc=50, scale=3)
```

若要從 T-SQL 呼叫此行的 Python，請在 `sp_execute_external_script` 的 Python 指令碼參數中新增 Python 函數。 輸出時應有資料框架，因此請使用 `pandas` 來進行轉換。

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=100, loc=50, scale=3));
'
    , @input_data_1 = N'   ;'
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

想要更輕鬆地產生一組不同的亂數？

與 SQL Server 合併時很容易做到。 您可以定義一個預存程序來取得使用者的引數，然後將這些引數當做變數傳遞至 Python 指令碼。

```sql
CREATE PROCEDURE MyPyNorm (
      @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import numpy
import pandas
OutputDataSet = pandas.DataFrame(numpy.random.normal(size=mynumbers, loc=mymean, scale=mysd));
'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- 第一行定義執行預存程序時所需要的每個 SQL 輸入參數。

- 開頭為 `@params` 的行會定義 Python 程式碼所使用的所有變數，以及對應的 SQL 資料類型。

- 緊接的行會將 SQL 參數名稱對應至相對應的 Python 變數名稱。

現在您已將 Python 函數包裝於預存程序中，您將可以輕鬆地呼叫函數並傳入不同的值，如下所示︰

```sql
EXECUTE MyPyNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-python-utility-functions-for-troubleshooting"></a>使用 Python 公用程式函數進行疑難排解

Python 套件提供各種公用程式函數來調查目前的 Python 環境。 如果您發現您的 Python 程式碼在 SQL Server 和外部環境中的執行方式不一致，這些函數會非常有用。

例如，您可以使用 `time` 套件中的系統計時函數來測量 Python 處理序所使用的時間量，並分析效能問題。

```sql
EXECUTE sp_execute_external_script
      @language = N'Python'
    , @script = N'
import time
start_time = time.time()

# Run Python processes

elapsed_time = time.time() - start_time
'
    , @input_data_1 = N' ;';
```

## <a name="next-steps"></a>後續步驟

若要在 SQL Server 中使用 Python 建立機器學習模型，請依照下列快速入門進行：

> [!div class="nextstepaction"]
> [快速入門：使用 SQL Server 機器學習服務在 Python 中建立預測模型並計算其分數](quickstart-python-train-score-model.md)

如需 SQL Server 機器學習服務的詳細資訊，請參閱：

- [什麼是 SQL Server 機器學習服務 (Python 和 R)？](../sql-server-machine-learning-services.md)
