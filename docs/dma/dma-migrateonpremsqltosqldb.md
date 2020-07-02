---
title: 使用 Data Migration Assistant，將 SQL Server 遷移至 Azure SQL Database
description: 瞭解如何使用 Data Migration Assistant 將內部部署 SQL Server 遷移至 Azure SQL Database
ms.date: 06/29/2020
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.custom: seo-lt-2019
ms.openlocfilehash: ec6b5ad0ab2047e72a1f3e3e5dfcd9fc49b954d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749783"
---
# <a name="migrate-on-premises-sql-server-or-sql-server-on-azure-vms-to-azure-sql-database-using-the-data-migration-assistant"></a>使用 Data Migration Assistant，將內部部署 SQL Server 或 Azure Vm 上的 SQL Server 遷移至 Azure SQL Database

Data Migration Assistant 提供 SQL Server 內部部署的順暢評量，並升級至較新版本的 SQL Server 或遷移至 Azure Vm 或 Azure SQL Database 上的 SQL Server。

本文提供逐步指示，說明如何使用 Data Migration Assistant，將內部部署 SQL Server 遷移至 Azure SQL Database。

## <a name="create-a-new-migration-project"></a>建立新的移轉專案

1. 在左窗格中，選取 [**新增**（+）]，然後選取 [**遷移**] 專案類型。

2. 將 [來源類型] 設定為**SQL Server** ，並將目標伺服器類型設為**Azure SQL Database**。

3. 選取 [建立]。

   ![建立遷移專案](../dma/media/NewCreate1.png)

## <a name="specify-the-source-server-and-database"></a>指定來源伺服器和資料庫

1. 針對 [來源]，在 [連線**至來源伺服器]** 底下的 [**伺服器名稱**] 文字方塊中，輸入來源 SQL Server 實例的名稱。

2. 選取來源 SQL Server 執行個體所支援的 [驗證類型]****。

   > [!NOTE]
   > 建議您選取 [連線**poperties**] 底下的 [**加密**連線] 核取方塊來加密連接。

    ![選取來源伺服器](../dma/media/select-source-server.png)

3. 選取 [連接]。

4. 選取要遷移至 Azure SQL Database 的單一源資料庫。

   > [!NOTE]
   > 如果您想要在進行遷移之前評估資料庫並查看並套用建議的修正，請選取 [**遷移前評估資料庫嗎？** ] 核取方塊。

    ![選取源資料庫](../dma/media/select-source-database.png)

5. 選取 [下一步]。

## <a name="specify-the-target-server-and-database"></a>指定目標伺服器和資料庫

1. 針對 [目標]，在 [**連接到目標伺服器]** 底下的 [**伺服器名稱**] 文字方塊中，輸入 Azure SQL Database 實例的名稱。 

2. 選取目標 Azure SQL Database 實例所支援的**驗證類型**。

   > [!NOTE]
   > 建議您選取 [連線**poperties**] 底下的 [**加密**連線] 核取方塊來加密連接。

     ![選取目標伺服器](../dma/media/select-target-server.png)

3. 選取 [連接]。

4. 選取要移轉至的單一目標資料庫。

   > [!NOTE]
   > 如果您想要遷移 Windows 使用者，請在 [**目標外部使用者功能變數名稱**] 文字方塊中，確定已正確指定目標外部使用者功能變數名稱。

    ![選取目標資料庫](../dma/media/select-target-database.png)

5. 選取 [下一步]。

## <a name="select-schema-objects"></a>選取結構描述物件

1. 從來源資料庫中，選取您要遷移至 Azure SQL Database 的結構描述物件。

    ![選取結構描述物件](../dma/media/select-schema-objects.png)

    > [!NOTE]
    > 有些無法原樣轉換的物件會出現自動修正機會。 按一下左窗格上的這些物件，可在右窗格上顯示建議的修正程式。 檢閱修正程式，並選擇套用或忽略所有變更 (逐一物件)。 請注意，套用或忽略某個物件的所有變更，並不會影響其他資料庫物件的變更。 無法轉換或自動修正的陳述式會重製到目標資料庫，並加上註解。

    ![建議的修正](../dma/media/suggested-fix.png)

2. 選取 **[一般 SQL 腳本**]。

3. 檢查產生的腳本。

    ![產生的腳本](../dma/media/generated-script.png)

## <a name="deploy-schema"></a>部署結構描述

1. 選取 [**部署架構**]。

2. 檢閱結構描述部署的結果。

    ![架構部署結果](../dma/media/schema-deployment-results.png)

3. 選取 [**遷移資料**] 以起始資料移轉程式。

4. 選取內含所要移轉資料的資料表。

    ![選取要遷移的資料表](../dma/media/select-tables-to-migrate.png) 

5. 選取 [**開始資料移轉**]。

最後一個畫面會顯示整體狀態。

   ![移轉狀態](../dma/media/migration-status.png) 

## <a name="see-also"></a>另請參閱

* [Data Migration Assistant (DMA)](../dma/dma-overview.md)
* [Data Migration Assistant：設定](../dma/dma-configurationsettings.md)
* [Data Migration Assistant：最佳做法](../dma/dma-bestpractices.md)
