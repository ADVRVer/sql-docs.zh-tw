---
title: "概觀和使用案例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62c964c5-eae4-4cf1-9024-d5a19adbd652
caps.latest.revision: 5
author: "jodebrui"
ms.author: "jodebrui"
manager: "jhubbard"
caps.handback.revision: 5
---
# 概觀和使用案例
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

記憶體內部 OLTP 是 SQL Server 和 Azure SQL Database 中提供的首要技術，可提高交易處理、資料擷取、資料載入及暫時性資料案例的效能。 本主題包含這項技術的概觀，並將概述記憶體內部 OLTP 的使用案例。 使用此資訊來判斷記憶體內部 OLTP 是否適合您的應用程式。 本主題隨附的範例會說明記憶體內部 OLTP 物件、效能示範的參考，以及您可在後續步驟中使用之資源的參考。


## <a name="in-memory-oltp-overview"></a>記憶體內部 OLTP 概觀

記憶體內部 OLTP 可以為正確的工作負載提供絕佳的效能提升。 有一位客戶 (bwin) 利用執行 SQL Server 2016 的電腦，運用記憶體內部 OLTP，設法[達到每秒 120 萬個要求數](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/)。 另一位客戶 (Quorum) 利用 Azure SQL Database 中的記憶體內部 OLTP，設法使其工作負載加倍，同時[減少 70% 的資源使用率](https://customers.microsoft.com/en-US/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database)。 當客戶已在某些案例中見識過最多 30 倍的效能提升時，您將見識到的提升程度會取決於工作負載。

現在，這個效能提升來自何處？ 在本質上，記憶體內部 OLTP 是藉由讓資料存取和交易執行更有效率，以及移除並行執行交易之間的鎖定和閂鎖競爭，來提升交易處理的效能︰因為它在記憶體內部，所以速度不快；因為它已針對記憶體內部的資料進行最佳化，所以速度很快。 資料儲存體、存取和處理演算法均已重新設計，可充分利用關於記憶體內部與高度並行運算的最新增強功能。

現在，只是因為資料存留於記憶體內部，不代表您會在發生失敗時遺失資料。 根據預設，所有交易都是完全持久的，表示您具有針對 SQL Server 中任何其他資料表所取得的相同持久性保證︰在交易認可時，所有變更都會寫入磁碟上的交易記錄檔。 如果在交易認可之後的任何時間發生失敗，當資料庫重新上線時，您的資料還是會在原處。 此外，記憶體內部 OLTP 會與 SQL Server 的所有高可用性和災害復原功能 (例如 AlwaysOn、備份/還原等) 一同運作。

若要在資料庫中利用記憶體內部 OLTP，您可以使用一或多個下列類型的物件：

- *記憶體最佳化資料表*是用於儲存使用者資料。 您可以在建立時將資料表宣告為記憶體最佳化。
- *非持久性資料表*是用於暫時性資料，可能是快取或中繼結果集 (取代傳統的暫存資料表)。 非持久性資料表是使用 DURABILITY=SCHEMA_ONLY 宣告的記憶體最佳化資料表，這表示對於這些資料表的變更不會造成任何 IO。 這可避免在無須顧慮持久性的情況下耗用了記錄 IO 資源。
- *記憶體最佳化資料表類型*是用於資料表值參數 (TVP)，以及預存程序中的中繼結果集。 這些可以用來代替傳統的資料表類型。 使用記憶體最佳化資料表類型宣告的資料表變數和 TVP，會繼承非持久性記憶體最佳化資料表的優點︰有效率的資料存取且沒有任何 IO。
- *原生編譯的 T-SQL 模組*是用來藉由減少 CPU 循環處理作業，進一步減少個別交易所需花費的時間。 您可以在建立時宣告要以原生方式編譯的 Transact-SQL 模組。 目前，下列 T-SQL 模組可以原生方式編譯︰預存程序、觸發程序和純量使用者定義函數。

記憶體內部 OLTP 內建於 SQL Server 和 Azure SQL Database 中。 此外，因為這些物件的行為與其傳統對應項目非常類似，您通常只需對資料庫和應用程式進行最少變更，就能獲得效能效益。 此外，您可以在相同資料庫中同時具有記憶體最佳化資料表和傳統以磁碟為基礎的資料表，並跨這兩個資料表執行查詢。 您將可在本主題結尾前找到一個 Transact-SQL 指令碼，其中會示範適用於這其中每一種類型物件的範例。

## <a name="usage-scenarios-for-in-memory-oltp"></a>記憶體內部 OLTP 的使用案例

記憶體內部 OLTP 並非神奇的快速按鈕，而且不適用於所有工作負載。 例如，如果大部分的查詢正在執行大範圍資料的彙總，則記憶體最佳化資料表將不會真正縮減您的 CPU 使用量 - 資料行存放區索引可協助此案例。

以下是我們曾見到客戶成功使用記憶體內部 OLTP 的案例和應用程式模式清單。

### <a name="high-throughput-and-low-latency-transaction-processing"></a>高輸送量且低延遲的交易處理

這真的是我們建置記憶體內部 OLTP 的核心案例︰為個別交易提供一致的低延遲，以支援大量交易。

常見的工作負載案例包括︰金融工具、體育博彩、行動遊戲及廣告投放的交易。 我們看到的另一個常見模式是經常讀取和/或更新的「目錄」。 有個範例是您具有大型檔案，每個檔案均分散於叢集中的一些節點上，而您會在記憶體最佳化資料表中，將每個檔案的每個分區位置編入目錄。

#### <a name="implementation-considerations"></a>實作考量

針對您的核心交易資料表 (亦即，含有效能最嚴重不足之交易的資料表)，使用記憶體最佳化資料表。 使用原生編譯的預存程序，以最佳化方式執行與商務交易相關聯的邏輯。 您可以向下推送到預存程序的邏輯越多，您可從記憶體內部 OLTP 中看見的效益就越多。

開始使用現有的應用程式：
1. 使用[交易效能分析報表](https://msdn.microsoft.com/library/dn205133.aspx)，以識別您想要移轉的物件， 
2. 以及使用[記憶體最佳化](https://msdn.microsoft.com/library/dn284308.aspx)和[原生編譯](https://msdn.microsoft.com/library/dn358355.aspx)建議程式來協助移轉。

#### <a name="customer-case-studies"></a>客戶案例研究

- CMC Markets 利用 SQL Server 2016 中的記憶體內部 OLTP 來達成一致的低延遲：[由於一秒太長而無法等待，這家金融服務公司目前正在更新其交易軟體。](https://customers.microsoft.com/en-us/story/because-a-second-is-too-long-to-wait-this-financial-services-firm-is-updating-its-trading-software)
- Durban 利用 SQL Server 2016 中的記憶體內部 OLTP 來支援增加的輸送量並處理尖峰工作負載：[當某家線上遊戲公司不想承擔其未來風險時，其首選為 SQL Server 2016。](https://customers.microsoft.com/en-us/story/when-an-online-gaming-company-doesnt-want-to-risk-its-future-it-bets-on-sql-server-2016)


### <a name="data-ingestion-including-iot-internet-of-things"></a>擷取資料，包括 IoT (Internet of Things)

記憶體內部 OLTP 真的很適合一次從許多不同來源擷取大量資料。 而且，相較於其他目的地，將資料擷取到 SQL Server 資料庫通常較有利，因為 SQL 會讓執資料的執行查詢速度變得非常快，並讓您能夠即時進行深入解析。

常見的應用程式模式是︰擷取感應器讀數和事件，來允許通知以及歷史資料分析。 管理批次更新 (即使是從多個來源也一樣)，同時降低並行讀取工作負載的影響。

#### <a name="implementation-considerations"></a>實作考量

使用記憶體最佳化資料表進行資料擷取。 如果擷取包含大部分的插入 (而非更新)，而且顧慮到資料的記憶體內部 OLTP 資料儲存體使用量，則可

- 使用工作，利用進行 `INSERT INTO <disk-based table> SELECT FROM <memory-optimized table>` 的工作，定期將資料批次卸載到含有[叢集資料行存放區索引](https://msdn.microsoft.com/library/gg492088.aspx)且磁碟為基礎的資料表，或者
- 使用[暫時的記憶體最佳化資料表](https://msdn.microsoft.com/library/mt590207.aspx)來管理歷程記錄資料 - 在此模式中，歷程記錄資料會存留於磁碟上，而資料移動是由系統所管理。

SQL Server 範例儲存機制包含智慧型格線應用程式，其會使用暫時的記憶體最佳化資料表、記憶體最佳化資料表類型及原生編譯的預存程序來加速資料擷取，同時管理感應器資料的記憶體內部 OLTP 儲存體使用量： 

 - [smart-grid-release](https://github.com/Microsoft/sql-server-samples/releases/tag/iot-smart-grid-v1.0) 
 - [smart-grid-source-code](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/iot-smart-grid)
 
#### <a name="customer-case-studies"></a>客戶案例研究

- [Quorum 利用 Azure SQL Database 中的記憶體內部 OLTP，將主要資料庫的工作負載加倍，同時降低 70% 的使用率](http://customers.microsoft.com/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database)
- EdgeNet 利用 SQL Server 2014 中的記憶體內部 OLTP，提升了批次資料載入的效能，並移除了維護中層快取的需求：[資料服務公司利用記憶體內部技術，即時存取產品資料](https://customers.microsoft.com/en-us/story/data-services-firm-gains-real-time-access-to-product-d)
- Beth Israel Deaconess Medical Center 利用 SQL Server 2014 中的記憶體內部 OLTP，已能大幅提升網域控制站的資料擷取率，並處理尖峰工作負載：[https://customers.microsoft.com/en-us/story/strengthening-data-security-and-creating-more-time-for]

### <a name="caching-and-session-state"></a>快取和工作階段狀態

記憶體內部 OLTP 技術讓 SQL 在維護工作階段狀態 (例如，針對 ASP.NET 應用程式) 和快取方面非常具有吸引力。

ASP.NET 工作階段狀態是非常成功的記憶體內部 OLTP 使用案例。 有一位客戶利用 SQL Server 達成了每秒 120 萬個要求數。 在此同時，他們已開始針對企業內所有中層應用程式的快取需求，使用所有記憶體內部 OLTP。 詳細資料︰[bwin 如何使用 SQL Server 2016 的記憶體內部 OLTP 來達到前所未有的效能和延展性](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/)

#### <a name="implementation-considerations"></a>實作考量

您可以將 BLOB 儲存 varbinary(max) 資料行中，藉以使用非持久性記憶體最佳化資料表做為簡單的索引鍵/值存放區。 或者，您可以在 SQL Server 和 Azure SQL Database 中，使用 [JSON 支援](https://azure.microsoft.com/blog/json-support-is-generally-available-in-azure-sql-database/)實作半結構化的快取。 最後，您可以透過具有完整關聯式結構描述 (其中包括各種資料類型和條件約束) 的非持久性資料表來建立完整關聯的快取。

利用 GitHub 上發行的指令碼來取代內建 SQL Server 工作階段狀態提供者所建立的物件，藉以開始使用記憶體最佳化的 ASP.NET 工作階段狀態：

- [aspnet-session-state](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/aspnet-session-state)

#### <a name="customer-case-studies"></a>客戶案例研究

- bwin 利用 SQL Server 2014 中的記憶體內部 OLTP，已能大幅增加輸送量並減少 ASP.NET 工作階段狀態的硬體使用量：[遊戲網站可以調整為每秒 250,000 個要求並提升玩家體驗](https://customers.microsoft.com/en-us/story/gaming-site-can-scale-to-250000-requests-per-second-an)
- bwin 甚至進一步利用 SQL Server 2016 中的記憶體內部 OLTP 來增加 ASP.NET 工作階段狀態的輸送量，並實作整個企業的中層快取系統：[bwin 如何使用 SQL Server 2016 的記憶體內部 OLTP 來達到前所未有的效能和延展性](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/)

### <a name="tempdb-object-replacement"></a>Tempdb 物件取代

利用非持久性資料表和記憶體最佳化資料表類型，來取代傳統以 tempdb 為基礎的 #temp 資料表、資料表變數和資料表值參數 (TVP)。

相較於傳統資料表變數和 #temp 資料表，記憶體最佳化資料表變數和非持久性資料表通常會減少 CPU，並完全移除記錄檔 IO。



#### <a name="implementation-considerations"></a>實作考量

若要開始使用，請參閱[使用記憶體最佳化提升暫存資料表與資料表變數效能。](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)

#### <a name="customer-case-studies"></a>客戶案例研究

- 有一位客戶只是將傳統 TVP 替換為記憶體最佳化 TVP，就能提升 40% 的效能： [在 Azure 中使用記憶體內部 OLTP 高速擷取 IoT 資料](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/04/07/a-technical-case-study-high-speed-iot-data-ingestion-using-in-memory-oltp-in-azure/)


### <a name="etl-extract-transform-load"></a>ETL (擷取轉換載入)

ETL 工作流程通常包含將資料載入暫存資料表、轉換資料，然後載入最終資料表。

#### <a name="implementation-considerations"></a>實作考量

針對資料暫存，使用非持久性記憶體最佳化資料表。 它們會完全移除所有的 IO，並讓資料存取更具效率。

如果您在暫存資料表上將轉換當成工作流程的一部分來執行，您可以使用原生編譯的預存程序來加速這些轉換。 如果您可以平行執行這些轉換，您就能從記憶體最佳化中取得其他擴充性效益。

## <a name="sample-script"></a>範例指令碼

開始使用記憶體內部 OLTP 之前，您需要建立 MEMORY_OPTIMIZED_DATA 檔案群組。 此外，我們建議使用資料庫相容性層級 130 (或更高層級)，並將資料庫選項 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT 設為 ON。

您可以在下列位置使用指令碼，在預設資料夾中建立檔案群組，並設定建議的設定：

- [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)

下列指令碼將說明您可以在資料庫中建立的記憶體內部 OLTP 物件：
  
     -- configure recommended DB option
     ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
     GO
     -- memory-optimized table
     CREATE TABLE dbo.table1
     ( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
       c2 NVARCHAR(MAX))
     WITH (MEMORY_OPTIMIZED=ON)
     GO
     -- non-durable table
     CREATE TABLE dbo.temp_table1
     ( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
       c2 NVARCHAR(MAX))
     WITH (MEMORY_OPTIMIZED=ON,
           DURABILITY=SCHEMA_ONLY)
     GO
     -- memory-optimized table type
     CREATE TYPE dbo.tt_table1 AS TABLE
     ( c1 INT IDENTITY,
       c2 NVARCHAR(MAX),
       is_transient BIT NOT NULL DEFAULT (0),
       INDEX ix_c1 HASH (c1) WITH (BUCKET_COUNT=1024))
     WITH (MEMORY_OPTIMIZED=ON)
     GO
     -- natively compiled stored procedure
     CREATE PROCEDURE dbo.usp_ingest_table1
       @table1 dbo.tt_table1 READONLY
     WITH NATIVE_COMPILATION, SCHEMABINDING
     AS
     BEGIN ATOMIC
         WITH (TRANSACTION ISOLATION LEVEL=SNAPSHOT,
               LANGUAGE=N'us_english')
     
       DECLARE @i INT = 1
     
       WHILE @i > 0
       BEGIN
         INSERT dbo.table1
         SELECT c2
         FROM @table1
         WHERE c1 = @i AND is_transient=0
     
         IF @@ROWCOUNT > 0
           SET @i += 1
         ELSE
         BEGIN
           INSERT dbo.temp_table1
           SELECT c2
           FROM @table1
           WHERE c1 = @i AND is_transient=1
     
           IF @@ROWCOUNT > 0
             SET @i += 1
           ELSE
             SET @i = 0
         END
       END
     
     END
     GO
     -- sample execution of the proc
     DECLARE @table1 dbo.tt_table1
     INSERT @table1 (c2, is_transient) VALUES (N'sample durable', 0)
     INSERT @table1 (c2, is_transient) VALUES (N'sample non-durable', 1)
     EXECUTE dbo.usp_ingest_table1 @table1=@table1
     SELECT c1, c2 from dbo.table1
     SELECT c1, c2 from dbo.temp_table1
     GO
   

## <a name="resources-to-learn-more"></a>值得深入了解的資源：

- [快速入門 1：可讓 T-SQL 擁有更快效能的記憶體內部 OLTP 技術](http://msdn.microsoft.com/library/mt694156.aspx)
- 如需使用記憶體內部 OLTP 的效能示範，請參閱：[in-memory-oltp-perf-demo-v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)
- [說明記憶體內部 OLTP 並顯示示範的 17 分鐘影片](https://www.youtube.com/watch?v=l5l5eophmK4) (示範是 8:25)
- [啟用記憶體內部 OLTP 並設定建議選項的指令碼](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)
- [主要的記憶體內部 OLTP 文件](https://msdn.microsoft.com/library/dn133186.aspx)
- [使用記憶體最佳化提升暫存資料表與資料表變數效能](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)
[在 SQL 資料庫中使用記憶體內部技術最佳化效能](https://docs.microsoft.com/azure/sql-database/sql-database-in-memory)
- [系統版本設定時態表與記憶體最佳化資料表](https://msdn.microsoft.com/library/mt590207.aspx)
-  [記憶體內部 OLTP - 一般工作負載模式和移轉考量](http://msdn.microsoft.com/library/dn673538.aspx)。 