---
title: WideWorldImporters 產生的資料-SQL 範例資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ace1f771ef3a77a6f7db0072442affe181d7872
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "37988942"
---
# <a name="wideworldimporters-data-generation"></a>WideWorldImporters 資料產生
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
WideWorldImporters 和 WideWorldImportersDW 資料庫發行的版本已從 2013 年 1 月 1 日到最多天的資料庫所產生的資料。

當您使用這些範例資料庫時，您可能想要包含較新的範例資料。

## <a name="data-generation-in-wideworldimporters"></a>WideWorldImporters 中的資料產生

若要產生到目前日期為止的範例資料：

1. 如果您還沒有這麼做，請安裝 WideWorldImporters 資料庫的全新版本。 如需安裝指示，請參閱[安裝和設定](wide-world-importers-oltp-install-configure.md)。
2. 在資料庫中執行下列陳述式：

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    此陳述式會將範例銷售和採購資料加入至資料庫，到目前日期為止。 它會顯示進度的資料產生每日。 產生資料可能需要約 10 分鐘每年所需的資料。 因為資料產生的隨機因素，有一些差異會產生執行之間的資料。

    若要增加或減少所產生的每日的訂單資料，請變更參數的值`@AverageNumberOfCustomerOrdersPerDay`。 使用參數`@SaturdayPercentageOfNormalWorkDay`和`@SundayPercentageOfNormalWorkDay`來判斷週末日期的訂單數量。

## <a name="import-generated-data-in-wideworldimportersdw"></a>WideWorldImportersDW 中產生的匯入資料

若要匯入到 WideWorldImportersDW OLAP 資料庫中目前的日期為止的範例資料：

1. 使用上一節中的步驟，WideWorldImporters OLTP 資料庫中執行資料產生邏輯。
2. 如果您還尚未這麼做，請安裝 WideWorldImportersDW 資料庫的全新版本。 如需安裝指示，請參閱[安裝和設定](wide-world-importers-oltp-install-configure.md)。
3. Reseed OLAP 資料庫，藉由在資料庫中執行下列陳述式：

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. 執行*每日 ETL.ispac*匯入資料至 OLAP 資料庫的 SQL Server Integration Services 封裝。 若要了解如何執行 ETL 作業，請參閱[WideWorldImporters ETL 工作流程](wide-world-importers-perform-etl.md)。

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>WideWorldImportersDW 中產生資料的效能測試

WideWorldImportersDW 可以任意增加效能測試的資料的大小。 比方說，它可以增加資料大小，以搭配叢集資料行存放區索引。

其中一項挑戰是將下載的大小夠小，無法下載輕鬆，但大型足以示範 SQL Server 效能功能。 比方說，只有當您使用較大的數字的資料列時，才會來達成顯著的優點，資料行存放區索引。 

您可以使用`Application.Configuration_PopulateLargeSaleTable`程序中的資料列數目增加`Fact.Sale`資料表。 資料列會插入在 2012年行事曆年，以避免與現有開始 2013 年 1 月 1 日的 World Wide Importers 資料衝突。

### <a name="procedure-details"></a>程序的詳細資料

#### <a name="name"></a>名稱

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>參數

  `@EstimatedRowsFor2012` **bigint** （具有預設值是 12000000）

#### <a name="result"></a>結果

大約所需的資料列數目會插入到`Fact.Sale`2012 年中的資料表。 此程序以人為方式限制為 50000，每日的資料列數目。 您可以變更這項限制，但限制可協助您避免意外 overinflations 的資料表。

此程序也適用於叢集資料行存放區索引，如果它尚未已經套用。
