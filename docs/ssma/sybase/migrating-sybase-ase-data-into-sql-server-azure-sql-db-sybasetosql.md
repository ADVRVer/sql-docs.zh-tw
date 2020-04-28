---
title: 將 Sybase ASE 資料移轉至 SQL Server-Azure SQL DB |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migrating data,Client Side Data Migration
- Migrating data,Server Side Data Migration
ms.assetid: 54a39f5e-9250-4387-a3ae-eae47c799811
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 28a07c08fd801a9d5fdcdde4206f7aa6fe7b926f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028842"
---
# <a name="migrating-sybase-ase-data-into-sql-server---azure-sql-db--sybasetosql"></a>將 Sybase ASE 資料移轉至 SQL Server-Azure SQL DB （SybaseToSQL）
成功將 Sybase 自我調整伺服器企業（ASE）資料庫物件載入[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 AZURE sql db 之後，您就可以將資料從 ASE 遷移至[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 azure sql db。  
  
> [!IMPORTANT]  
> 如果所使用的引擎是伺服器端資料移轉引擎，則在您遷移資料之前，您必須在執行 SSMA 的電腦上安裝 SSMA for Sybase ASE Extension Pack 和 Sybase ASE 提供者。 SQL Server Agent 服務也必須正在執行。 如需有關如何安裝延伸模組套件的詳細資訊，請參閱[在 SQL Server 上安裝 SSMA 元件（SybaseToSQL）](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
## <a name="setting-migration-options"></a>設定遷移選項  
將資料移轉至[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 AZURE SQL DB 之前，請先參閱 [**專案設定**] 對話方塊中的專案遷移選項。  
  
-   藉由使用此對話方塊，您可以設定選項，例如遷移批次大小、資料表鎖定、條件約束檢查、null 值處理和識別值處理。 如需專案遷移設定的詳細資訊，請參閱[專案設定（遷移）（Sybase）](https://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924)。  
  
    如需有關**擴充資料移轉設定**的詳細資訊，請參閱[資料移轉設定](data-migration-settings-sybasetosql.md)  
  
-   [**專案設定**] 對話方塊中的 [**遷移引擎**] 可讓使用者使用兩種類型的資料移轉引擎（視覺效果）來執行遷移程式：  
  
    1.  用戶端資料移轉引擎  
  
    2.  伺服器端資料移轉引擎  
  
**用戶端資料移轉：**  
  
-   若要在用戶端起始資料移轉，請在 [**專案設定**] 對話方塊中選取 [**用戶端資料移轉引擎**] 選項。  
  
-   在 [**專案設定**] 中，預設會設定 [**用戶端資料移轉引擎**] 選項。  
  
    > [!NOTE]  
    > 用戶端資料移轉引擎位於 SSMA 應用程式內，因此不會相依于延伸模組套件的可用性。  
  
**伺服器端資料移轉：**  
  
-   在伺服器端資料移轉期間，引擎位於目標資料庫上。 它是透過延伸模組套件進行安裝。 如需有關如何安裝延伸模組套件的詳細資訊，請參閱[在 SQL Server 上安裝 SSMA 元件（SybaseToSQL）](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
-   若要在伺服器端起始遷移，請在 [**專案設定**] 對話方塊中選取 [**伺服器端資料移轉引擎**] 選項。  
  
> [!NOTE]  
> 當 Azure SQL DB 作為目標資料庫使用時，只會允許**用戶端資料移轉**，而且不支援伺服器端資料移轉。  
  
## <a name="migrating-data-to-sql-server-or-azure-sql-db"></a>將資料移轉至 SQL Server 或 Azure SQL DB  
遷移資料是大量載入作業，會將資料列從 ASE 資料表移至交易中 SQL Server 資料表。 每筆交易中載入 SQL Server 或 Azure SQL DB 的資料列數目，會在專案設定中進行設定。  
  
若要查看遷移訊息，請確定 [輸出] 窗格是可見的。 否則，請從 [ **View** ] 功能表選取 [**輸出**]。  
  
**遷移資料**  
  
1.  驗證下列項目：  
  
    -   ASE 提供者會安裝在執行 SSMA 的電腦上。  
  
    -   您已將已轉換的物件與目標資料庫（SQL Server 或 Azure SQL DB）同步處理。  
  
2.  在 [Sybase Metadata Explorer] 中，選取包含您想要遷移之資料的物件：  
  
    -   若要遷移所有架構的資料，請選取 [**架構**] 旁的核取方塊。  
  
    -   若要遷移資料或省略個別的資料表，請先展開架構，展開 [**資料表**]，然後選取或清除資料表旁的核取方塊。  
  
3.  若要遷移資料，會發生兩種情況：  
  
    **用戶端資料移轉：**  
  
    若要執行**用戶端資料移轉**，請在 [**專案設定**] 對話方塊中選取 [**用戶端資料移轉引擎**] 選項。  
  
    **伺服器端資料移轉：**  
  
    -   執行伺服器端資料移轉之前，請確定：  
  
        1.  SSMA for Sybase Extension Pack 安裝在 SQL Server 的實例上。  
  
        2.  SQL Server Agent 服務正在的實例上執行 SQL Server  
  
    -   針對執行**伺服器端資料移轉**，請在 [**專案設定**] 對話方塊中選取 [**伺服器端資料移轉引擎**] 選項。  
  
4.  以滑鼠右鍵按一下 Sybase Metadata Explorer 中的 [**架構**]，然後按一下 [**遷移資料**]。 您也可以遷移個別物件或物件類別的資料：以滑鼠右鍵按一下物件或其父資料夾，然後選取 [**遷移資料**] 選項。  
  
    > [!NOTE]  
    > 如果 SQL Server 的實例上未安裝 Sybase 延伸模組套件的 SSMA，而且已選取 [**伺服器端資料移轉引擎**]，則在將資料移轉至目標資料庫時，會發生下列錯誤：「在 SQL Server 上找不到 SSMA 資料移轉元件，將無法進行伺服器端資料移轉。 請檢查是否已正確安裝延伸模組套件」。 按一下 [**取消**] 以終止資料移轉。  
  
5.  在 [**連接到 SYBASE ASE** ] 對話方塊中，輸入連接認證，然後按一下 **[連接]**。 如需連接到 Sybase ASE 的詳細資訊，請參閱[連接到 sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md)  
  
    如果目標資料庫是 SQL Server，請在 [**連接到 SQL Server** ] 對話方塊中輸入連接認證，然後按一下 **[連接]**。 如需連接到 SQL Server 的詳細資訊，請參閱[連接到 SQL Server （SybaseToSQL）](https://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)  
  
    如果目標資料庫是 Azure SQL DB，請在 [**連接到 AZURE SQL db** ] 對話方塊中輸入連線認證，然後按一下 **[連線]**。 如需有關連接至 Azure SQL DB 的詳細資訊，請參閱連線[到 AZURE SQL db &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
    訊息將會出現在 [**輸出**] 窗格中。 當遷移完成時，就會顯示**資料移轉報表**。 如果有任何資料未遷移，請按一下包含錯誤的資料列，然後按一下 [**詳細**資料]。 當您完成報表時，請按一下 [**關閉**]。 如需資料移轉報告的詳細資訊，請參閱[資料移轉報告（SSMA 一般）](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> 當 SQL Express edition 做為目標資料庫使用時，只允許用戶端資料移轉，而且不支援伺服器端資料移轉。  
  
## <a name="see-also"></a>另請參閱  
[將 Sybase ASE 資料庫移轉至 SQL Server-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
