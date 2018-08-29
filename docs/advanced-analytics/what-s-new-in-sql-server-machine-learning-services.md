---
title: 什麼&#39;的新功能 SQL Server 機器學習服務 |Microsoft Docs
description: 新功能通知每個版本的 SQL Server 2016 R Services、 R Server、 SQL Server 2017 Machine Learning 服務。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8d3dc4c730ea9c7c9ba0126a50ed4bb8129efc9c
ms.sourcegitcommit: fb269accc3786715c78f8b6e2ec38783a6eb63e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43152578"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>什麼是 SQL Server Machine Learning 服務的新功能 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

機器學習服務功能會隨著我們持續展開、 擴充和強化的資料平台與資料科學，analytics 之間的整合至 SQL Server 加入每個版本中，並監督式的學習您想要實作您的資料。 

## <a name="new-in-sql-server-2017"></a>SQL Server 2017 的新功能

此版本新增了[的 Python 支援和領先業界的機器學習服務演算法](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)。 重新命名以反映新的範圍，SQL Server 2017 標示了[SQL Server Machine Learning 服務 （資料庫）](what-is-sql-server-machine-learning.md)，使用 Python 和 r 語言支援 

此版也導入了[SQL Server Machine Learning Server （獨立式）](r/r-server-standalone.md)、 完全獨立的 SQL Server，針對您想要在專用的系統上執行的 R 和 Python 工作負載。 獨立伺服器，與您發佈及調整而不需使用 SQL Server 的 R 或 Python 的解決方案。

### <a name="python-integration-for-in-database-analytics"></a>在資料庫內分析 Python 整合

T-SQL 和 Python 的整合現在支援透過[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)系統預存程序。 您可以呼叫任何使用此預存程序的 Python 程式碼。 在安全的雙重的架構，可讓企業級部署 Python 模型及指令碼，可從應用程式使用簡單的預存程序呼叫中執行程式碼。 從 SQL Python 程序和 MPI 通道平行處理的資料流處理資料，可達到進一步提高效能。

您可以使用 T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md)函式來執行[原生評分](sql-native-scoring.md)上預先定型的模型，就已經先前儲存在所需的二進位格式。

### <a name="python-libraries"></a>Python 程式庫

| 封裝 | 描述 |
|---------|-------------|
[**revoscalepy**](python/what-is-revoscalepy.md)| RevoScaleR 的 Python 相當。 您可以建立用於線性及羅吉斯迴歸、 決策樹、 梯度上升的樹和隨機樹系，所有可平行執行，且能夠在遠端計算內容中執行的 Python 模型。 此套件支援使用多個資料來源和遠端計算內容。 資料科學家或開發人員可以執行 Python 程式碼的遠端 SQL 伺服器上，瀏覽資料，或建立模型，而不移動資料。 |
|[**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) |Python 相當的 MicrosoftML R 封裝。 |

### <a name="r-libraries"></a>R 程式庫

| 封裝 | 描述 |
|---------|-------------|
| [**MicrosoftML (R)**](using-the-microsoftml-package.md) | 新狀態機器學習演算法和資料轉換可以縮放或執行在遠端計算內容。 演算法會包括可自訂的深度類神經網路、 迅速的決策樹及決策樹、 線性迴歸和羅吉斯迴歸。  |
| [**R 封裝管理**](r/install-additional-r-packages-on-sql-server.md) | 增強在此版本中，具有下列優點： 資料庫角色來協助管理套件，並指派權限才能安裝封裝，DBA [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)中協助 dba 在遇到管理套件，而不需要的 T-SQL 陳述式不需要知道 R 和一組豐富的中的 R 函數[RevoScaleR](r/use-revoscaler-to-manage-r-packages.md)幫助您安裝、 移除或列出的封裝，使用者所擁有。 |

### <a name="pre-trained-models"></a>預先定型的模型

[**預先定型的模型**](install/sql-pretrained-models-install.md)可供 Python 和。 使用影像辨識和正負面情感分析，這些模型來產生預測，根據您的資料。 


## <a name="new-in-sql-server-2016"></a>SQL Server 2016 的新功能

這個的版導入了機器學習服務透過 SQL server 的功能**SQL Server 2016 R Services**，處理 R 指令碼中的資料庫引擎執行個體的常駐資料的資料庫內分析引擎。

此外， **SQL Server 2016 R Server （獨立式）** 做為 Windows 伺服器上安裝 R Server 的方式發行。 一開始，SQL Server 安裝程式會提供唯一的方式，來安裝 R Server for Windows。 在更新版本中，開發人員和想要在 Windows 上的 R 伺服器的資料科學家可以使用另一個獨立安裝程式來達到相同的目標。 在 SQL Server 的獨立伺服器和獨立的伺服器產品的功能上相當[Microsoft R Server for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)。

| 版本 |功能更新 |
|---------|----------------|
| CU 的新增項目 | [**即時計分**](real-time-scoring.md)依賴原生 c + + 程式庫，以讀取最佳化的二進位格式，儲存在模型，則不必呼叫 R 執行階段產生預測。 這可讓評分作業更快。 使用即時評分，您可以執行預存程序，或執行 R 程式碼的即時評分。 即時評分也會提供適用於 SQL Server 2016 中，如果執行個體已升級至最新版本的[!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]。 |
| 最初發行 | [**R 的資料庫內分析整合**](r/sql-server-r-services.md)。 <br/><br/> 在 T-SQL，反之亦然，函式呼叫 R 的 R 套件。 RevoScaleR 函式提供大規模的 R 分析區塊資料處理成元件部分，協調和管理分散式處理和彙總結果。 在 SQL Server 2016 R Services （資料庫），與 database engine 執行個體，brining 資料和分析，一起在相同的處理內容中整合 RevoScaleR 引擎。 <br/><br/>透過 T-SQL 和 R 整合[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)。 您可以呼叫任何使用此預存程序的 R 程式碼。 這個安全的基礎結構可讓企業級部署 Rn 模型和您可以從使用簡單的預存程序的應用程式呼叫的指令碼。 從 SQL R 處理序和 MPI 通道平行處理的資料流處理資料，可達到進一步提高效能。 <br/><br/>您可以使用 T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md)函式來執行[原生評分](sql-native-scoring.md)上預先定型的模型，就已經先前儲存在所需的二進位格式。|

## <a name="linux-support-roadmap"></a>Linux 支援藍圖

使用 R 或 Python 資料庫內的機器學習服務目前不支援在 Linux 上的 SQL Server。 尋找未來版本中的宣告。

不過，在 Linux 上您可以執行[原生評分](sql-native-scoring.md)使用 T-SQL 的預測函數。 原生評分，可讓您從預先定型的模型非常快速，而不需要呼叫，或甚至需要 R 執行階段進行評分。 這表示您可以在 Linux 上使用 SQL Server，來產生預測非常快速，以提供用戶端應用程式。

<a name="azure-sql-database-roadmap"></a>

## <a name="azure-sql-database-roadmap"></a>Azure SQL Database 的藍圖

沒有適用於 Azure SQL Database 中的 R 有限的支援： 僅適用於美國中部等美國，在進階層所建立的服務中。 展開的涵蓋範圍，包括 Python 支援，很可能在未來版本中遵循。 不過，這次沒有預訂的正式發行日期。  

## <a name="next-steps"></a>後續步驟

+ [安裝 SQL Server 2017 Machine Learning 服務 （資料庫）](install/sql-machine-learning-services-windows-install.md)
+ [機器學習服務教學課程和範例](tutorials/machine-learning-services-tutorials.md)
