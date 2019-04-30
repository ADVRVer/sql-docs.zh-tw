---
title: 快速入門：連線及查詢 Azure SQL 資料倉儲
titleSuffix: Azure Data Studio
description: 本快速入門示範如何使用 Azure Data Studio 連接到 Azure SQL 資料倉儲，並執行查詢
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 72e7e0e83757b52ba7fba6a24cc91499ca4863b1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63143869"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>快速入門：使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]連線及查詢 Azure SQL 資料倉儲中的資料

本快速入門示範如何使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]連接到 Azure SQL 資料倉儲，然後使用 TRANSACT-SQL 陳述式來建立、插入和選取資料。 

## <a name="prerequisites"></a>必要條件
若要完成本快速入門中，您需要[!INCLUDE[name-sos](../includes/name-sos-short.md)]，和 Azure SQL 資料倉儲。

- [安裝[!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md)。

如果您還沒有 SQL 資料倉儲，請參閱[建立 SQL 資料倉儲](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision)。

請記得登入認證與伺服器名稱 ！


## <a name="connect-to-your-data-warehouse"></a>連接到您的資料倉儲

使用 [!INCLUDE[name-sos](../includes/name-sos-short.md)] 連接 Azure SQL 資料倉儲伺服器。

1. 第一次執行[!INCLUDE[name-sos](../includes/name-sos-short.md)]時應該會開啟**連接**頁面。 如果您沒有看到**連接**頁面，按一下**加入連接**，或**伺服器**資訊看板中的**新增連線**圖示：
   
   ![新的 [連線] 圖示](media/quickstart-sql-dw/new-connection-icon.png)

2. 本文使用 *SQL 登入*，但也支援 *Windows 驗證*。 如下表所示，填入*您*的 Azure SQL server 所使用的伺服器名稱、使用者名稱和密碼:

   | 設定       | 建議值 | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **伺服器名稱** | 完整伺服器名稱 | 名稱應該類似下面的： **sqldwsample.database.windows.net** |
   | **驗證** | SQL 登入| 本教學課程中使用 SQL 驗證。 |
   | **使用者名稱** | 伺服器系統管理員帳戶 | 這是您在建立伺服器時指定的帳戶。 |
   | **密碼 (SQL 登入)** | 伺服器系統管理員帳戶的密碼 | 這是您在建立伺服器時指定的密碼。 |
   | **儲存密碼嗎？** | [是] 或 [否] | 如果您不想每次輸入密碼，請選取 [是]。 |
   | **資料庫名稱** | *保留空白* | 要連線之資料庫的名稱。 |
   | **伺服器群組** | 選取 <Default> | 如果您建立伺服器群組，您可以設定為特定的伺服器群組。 | 

   ![新的 [連線] 圖示](media/quickstart-sql-dw/new-connection-screen.png) 

3. 如果您的伺服器沒有防火牆規則來允許連線，Azure Data Studio**建立新的防火牆規則**表單隨即開啟。 請完成表單，以建立新的防火牆規則。 如需詳細資訊，請參閱[防火牆規則](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)。

   ![新的防火牆規則](media/quickstart-sql-dw/firewall.png)  

4. 成功連接後，您的伺服器便會在*伺服器*資訊看板中開啟。

## <a name="create-the-tutorial-data-warehouse"></a>建立教學課程的資料倉儲
1. 在 [物件總管] 中以滑鼠右鍵按一下您的伺服器，然後選取**新增查詢。**

1. 將下列程式碼片段貼到查詢編輯器，然後按一下**執行**:

   ```sql
    IF NOT EXISTS (
       SELECT name
       FROM sys.databases
       WHERE name = N'TutorialDB'
    )
    CREATE DATABASE [TutorialDB] (EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');
    GO  
    
    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
   ```


## <a name="create-a-table"></a>建立資料表

查詢編輯器仍然會連線到*master*資料庫，但我們想要在*TutorialDB*資料庫中建立資料表。 

1. 變更連接內容為**TutorialDB**:

   ![變更內容](media/quickstart-sql-database/change-context.png)


1. 將下列程式碼片段貼到查詢編輯器，然後按一下**執行**:

   > [!NOTE]
   > 您可以將程式碼片段附加或覆寫先前編輯器中的查詢。 請注意，按一下**執行**只會執行已選取的查詢。 如果未選取，按一下**執行**將執行編輯器中所有的查詢。

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT     NOT NULL,
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows"></a>插入資料列

1. 將下列程式碼片段貼到查詢編輯器，然後按一下**執行**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```


## <a name="view-the-result"></a>檢視結果
1. 將下列程式碼片段貼到查詢編輯器，然後按一下**執行**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. 查詢的結果會顯示：

   ![選取 [結果]](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>清除資源

在此系列文章中其他的文章建立在本快速入門之上。 如果您打算繼續實作後續的快速入門，請勿清除本快速入門中建立的資源。  如果您不打算繼續，請使用下列步驟刪除本快速入門在 Azure 入口網站所建立的資源。
清除資源，藉由刪除您不再需要的資源群組。 如需詳細資訊，請參閱 <<c0> [ 清除資源](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources)。


## <a name="next-steps"></a>後續的步驟

既然您已成功連線到 Azure SQL 資料倉儲，並執行查詢，試試看[教學課程中的程式碼編輯器](tutorial-sql-editor.md)。
