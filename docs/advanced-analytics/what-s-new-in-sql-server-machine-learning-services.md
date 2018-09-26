---
title: 什麼&#39;的新功能 SQL Server 機器學習服務 |Microsoft Docs
description: 新功能通知每個版本的 SQL Server 2016 R Services、 R Server、 SQL Server 2017 Machine Learning 服務。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: c6df8f09d46b2f90c1cd464b6e80cda20e83c97f
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712571"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>什麼是 SQL Server Machine Learning 服務的新功能 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

機器學習服務功能會新增至 SQL Server 各版本隨著我們持續展開、 擴充和強化的資料平台、 進階的分析與資料科學之間的整合。 

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2019-preview"></a>SQL Server 2019 preview 的新功能

此版本新增 SQL Server 中的 R 和 Python 機器學習服務作業的呼聲最高的功能。 如需所有在此版本中功能的詳細資訊，請參閱[What's New in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)並[Release Notes for SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md)。

| 版本 | 功能更新 |
|---------|----------------|
| CTP 2.0 | R 和 Python 機器學習服務，再加上新的 Java 延伸模組的 Linux 平台支援。 如需入門的說明，請參閱[安裝 SQL Server Machine Learning 服務在 Linux 上](../linux/sql-server-linux-setup-machine-learning.md)。 |
| CTP 2.0 | [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)包含兩個新的參數可讓您輕鬆地從資料分割的資料產生多個模型。 進一步了解本教學課程[在 R 中建立資料分割為基礎的模型](tutorials/r-tutorial-create-models-per-partition.md)。 |
| CTP 2.0 | 容錯移轉叢集支援現在支援 Windows 和 Linux，假設所有節點上啟動 SQL Server Launchpad 服務。 如需詳細資訊，請參閱 < [SQL Server 容錯移轉叢集安裝](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)。 |
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2017"></a>SQL Server 2017 的新功能

此版本新增了[的 Python 支援和領先業界的機器學習服務演算法](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)。 重新命名以反映新的範圍，SQL Server 2017 標示了[SQL Server Machine Learning 服務 （資料庫）](what-is-sql-server-machine-learning.md)，使用 Python 和 r 語言支援 

功能通知所有總，請參閱[What's New in SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)。

### <a name="r-enhancements"></a>R 的增強功能

SQL Server 2017 Machine Learning 服務的 R 元件是新一代的 SQL Server 2016 R Services，基底 R、 RevoScaler 和其他套件的更新版本。

適用於 R 的新功能包括[**套件管理**](r/install-additional-r-packages-on-sql-server.md)，具有下列優點： 

+ 資料庫角色可協助 Dba 管理封裝，以及指派安裝套件的權限。
+ [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)協助 Dba 會管理在熟悉的 T-SQL 語言中的封裝。
+ [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md)函式說明安裝時，使用者所擁有的移除或列出的套件。 如需詳細資訊，請參閱 <<c0> [ 如何使用 RevoScaleR 函數來尋找或安裝 R 封裝在 SQL Server 上](r/use-revoscaler-to-manage-r-packages.md)。

### <a name="r-libraries"></a>R 程式庫

| 封裝 | 描述 |
|---------|-------------|
| [**MicrosoftML**](using-the-microsoftml-package.md) | 在此版本中，MicrosoftML 包含在預設 R 安裝中，刪除在先前的 SQL Server 2016 R Services 所需的升級步驟。 MicrosoftML 提供的圖案狀態機器學習服務演算法和可調整，或在遠端計算內容中執行資料轉換。 演算法會包括可自訂的深度類神經網路、 迅速的決策樹及決策樹、 線性迴歸和羅吉斯迴歸。  |

### <a name="python-integration-for-in-database-analytics"></a>在資料庫內分析 Python 整合

Python 是機器的一種語言，可提供很大的彈性和各種不同學習工作的能力。 適用於 Python 的開放原始碼程式庫包含數個平台，可自訂的類神經網路，以及熱門的程式庫進行自然語言處理。 現在，在 SQL Server 2017 Machine Learning 中支援這個廣泛使用的語言。

因為 Python 會與 database engine 整合，您可以讓分析貼近資料，並排除與移動資料相關聯的安全性風險與成本。 您可以部署使用 Visual Studio 等工具的 Python 為基礎的機器學習解決方案。 生產應用程式可以取得模型的預測，或視覺效果的 Python 3.5 執行階段使用 SQL Server 資料存取方法。

T-SQL 和 Python 整合透過支援[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)系統預存程序。 您可以呼叫任何使用此預存程序的 Python 程式碼。 在安全的雙重的架構，可讓企業級部署 Python 模型及指令碼，可從應用程式使用簡單的預存程序呼叫中執行程式碼。 從 SQL Python 程序和 MPI 通道平行處理的資料流處理資料，可達到進一步提高效能。

您可以使用 T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md)函式來執行[原生評分](sql-native-scoring.md)上預先定型的模型，就已經先前儲存在所需的二進位格式。

### <a name="python-libraries"></a>Python 程式庫

| 封裝 | 描述 |
|---------|-------------|
[**revoscalepy**](python/what-is-revoscalepy.md)| RevoScaleR 的 Python 相當。 您可以建立用於線性及羅吉斯迴歸、 決策樹、 梯度上升的樹和隨機樹系，所有可平行執行，且能夠在遠端計算內容中執行的 Python 模型。 此套件支援使用多個資料來源和遠端計算內容。 資料科學家或開發人員可以執行 Python 程式碼的遠端 SQL 伺服器上，瀏覽資料，或建立模型，而不移動資料。 |
|[**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) |Python 相當的 MicrosoftML R 封裝。 |

### <a name="pre-trained-models"></a>預先定型的模型

[**預先定型的模型**](install/sql-pretrained-models-install.md)可供 Python 和。 使用影像辨識和正負面情感分析，這些模型來產生預測，根據您的資料。 

### <a name="standalone-server-as-a-shared-feature-in-sql-server-setup"></a>做為共用的功能，在 SQL Server 安裝程式的獨立伺服器

此版本也加入[SQL Server Machine Learning Server （獨立式）](r/r-server-standalone.md)，完全獨立的資料科學伺服器，支援 R 和 Python 中的統計和預測性分析。 如同 R Services，此伺服器是新版的 SQL Server 2016 R Server （獨立式）。 獨立伺服器，與您發佈及調整 SQL Server 上的 R 或 Python 的解決方案，不含相依性。
::: moniker-end

## <a name="new-in-sql-server-2016"></a>SQL Server 2016 的新功能

這個的版導入了機器學習服務透過 SQL server 的功能**SQL Server 2016 R Services**，處理 R 指令碼中的資料庫引擎執行個體的常駐資料的資料庫內分析引擎。

此外， **SQL Server 2016 R Server （獨立式）** 做為 Windows 伺服器上安裝 R Server 的方式發行。 一開始，SQL Server 安裝程式會提供唯一的方式，來安裝 R Server for Windows。 在更新版本中，開發人員和想要在 Windows 上的 R 伺服器的資料科學家可以使用另一個獨立安裝程式來達到相同的目標。 在 SQL Server 的獨立伺服器和獨立的伺服器產品的功能上相當[Microsoft R Server for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)。

功能通知所有總，請參閱[What's New in SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)。

| 版本 |功能更新 |
|---------|----------------|
| CU 的新增項目 | [**即時計分**](real-time-scoring.md)依賴原生 c + + 程式庫，以讀取最佳化的二進位格式，儲存在模型，則不必呼叫 R 執行階段產生預測。 這可讓評分作業更快。 使用即時評分，您可以執行預存程序，或執行 R 程式碼的即時評分。 即時評分也會提供適用於 SQL Server 2016 中，如果執行個體已升級至最新版本的[!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]。 |
| 最初發行 | [**R 的資料庫內分析整合**](r/sql-server-r-services.md)。 <br/><br/> 在 T-SQL，反之亦然，函式呼叫 R 的 R 套件。 RevoScaleR 函式提供大規模的 R 分析區塊資料處理成元件部分，協調和管理分散式處理和彙總結果。 在 SQL Server 2016 R Services （資料庫），與 database engine 執行個體，brining 資料和分析，一起在相同的處理內容中整合 RevoScaleR 引擎。 <br/><br/>透過 T-SQL 和 R 整合[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)。 您可以呼叫任何使用此預存程序的 R 程式碼。 這個安全的基礎結構可讓企業級部署 Rn 模型和您可以從使用簡單的預存程序的應用程式呼叫的指令碼。 從 SQL R 處理序和 MPI 通道平行處理的資料流處理資料，可達到進一步提高效能。 <br/><br/>您可以使用 T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md)函式來執行[原生評分](sql-native-scoring.md)上預先定型的模型，就已經先前儲存在所需的二進位格式。|

## <a name="linux-support-roadmap"></a>Linux 支援藍圖

當您安裝的機器學習服務與資料庫引擎執行個體的封裝時，SQL Server 2019 CTP 2.0 會新增 R、 Python 和 Java 的 Linux 支援。 如需詳細資訊，請參閱 <<c0> [ 安裝 SQL Server Machine Learning 服務在 Linux 上](../linux/sql-server-linux-setup-machine-learning.md)。

在 Linux 上，SQL Server 2017 沒有 R 或 Python 整合，但您可以使用[原生評分](sql-native-scoring.md)Linux 上因為該功能是透過 T-SQL [PREDICT]()，以在 Linux 上執行。 原生評分，可讓高效能評分從預先定型的模型，而不需要呼叫，或甚至需要 R 執行階段。

<a name="azure-sql-database-roadmap"></a>

## <a name="azure-sql-database-roadmap"></a>Azure SQL Database 的藍圖

目前沒有 Machine Learning 服務 （R 和 Python） Azure SQL Database 中支援。 正在規劃支援，但這次沒有預訂的正式發行日期。  

## <a name="next-steps"></a>後續步驟

+ [安裝 SQL Server 2017 Machine Learning 服務 （資料庫）](install/sql-machine-learning-services-windows-install.md)
+ [機器學習服務教學課程和範例](tutorials/machine-learning-services-tutorials.md)
