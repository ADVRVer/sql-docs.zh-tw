---
title: "規劃在 SQL Server 中採用記憶體內部 OLTP 功能 | Microsoft Docs"
ms.custom: ""
ms.date: "10/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 041b428f-781d-4628-9f34-4d697894e61e
caps.latest.revision: 4
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 3
---
# 規劃在 SQL Server 中採用記憶體內部 OLTP 功能
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]


這篇文章說明記憶體內部功能的採用方式對商務系統的其他方面有何影響。



## A. 採用記憶體內部 OLTP 功能


下列小節將討論您計劃採用及實作記憶體內部功能時，您必須考慮的因素。 許多說明資訊位於︰

- [使用記憶體內部 OLTP 改善 Azure SQL Database 中的應用程式效能](https://azure.microsoft.com/documentation/articles/sql-database-in-memory-oltp-migration/)



### A.1 必要條件

使用記憶體內部功能的一項必要條件，可能需要 SQL 產品的版本或服務層。 如需這項與其他必要條件，請參閱︰

- [使用記憶體最佳化資料表的需求](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)
    - [SQL Server 2016 的版本和元件](../../sql-server/editions-and-components-of-sql-server-2016.md)
    - [SQL Database 定價層建議](https://azure.microsoft.com/documentation/articles/sql-database-service-tier-advisor/)


### A.2 預測使用中的記憶體數量

您的系統是否有足夠的使用中記憶體，可以支援新的記憶體最佳化資料表？

#### Microsoft SQL Server

記憶體最佳化資料表，其中包含 200 GB 的資料，需要超過 200 GB 的使用中記憶體專門用來支援它。 實作包含大量資料的記憶體最佳化資料表之前，您必須預測可能需要新增至伺服器電腦的額外使用中記憶體數量。 如需估計指引，請參閱︰

- [估計記憶體最佳化資料表的記憶體需求](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)

#### Azure SQL Database

對於裝載於 Azure SQL Database 雲端服務的資料庫，您所選的服務層會影響資料庫允許使用的使用中記憶體數量。 您應該規劃使用警示來監視資料庫的記憶體使用量。 如需詳細資料，請參閱：

- [監視記憶體內部 OLTP 儲存體](https://azure.microsoft.com/documentation/articles/sql-database-in-memory-oltp-monitoring/)

#### 記憶體最佳化資料表變數

宣告為記憶體最佳化的資料表變數有時候會比位於 **tempdb** 資料庫的傳統 #TempTable 更適合。 這類資料表變數可以大幅提升效能，而不必使用大量的使用中記憶體。

### A.3 資料表必須離線，才能轉換成記憶體最佳化

某些 ALTER TABLE 功能適用於記憶體最佳化資料表。 但您無法發出 ALTER TABLE 陳述式將以磁碟為基礎的資料表轉換成記憶體最佳化資料表。 相反地，您必須使用一組更手動化的步驟。 下面是您可以將以磁碟為基礎的資料表轉換成記憶體最佳化的各種方式。

#### 手動撰寫指令碼

將以磁碟為基礎的資料表轉換成記憶體最佳化資料表的方法之一，是自行撰寫所需的 Transact-SQL 步驟。


1. 暫停應用程式活動。

2. 進行完整備份。

3. 重新命名以磁碟為基礎的資料表。

4. 發出 CREATE TABLE 陳述式來建立新的記憶體最佳化資料表。

5. INSERT INTO (插入) 記憶體最佳化資料表，並同時對以磁碟為基礎的資料表使用 SELECT FROM。

6. DROP (卸除) 以磁碟為基礎的資料表。

7. 進行另一個完整備份。

8. 繼續應用程式活動。


#### 記憶體最佳化 Advisor

「記憶體最佳化建議程式」工具可以產生指令碼，以協助實作將以磁碟為基礎的資料表轉換成記憶體最佳化資料表。 此工具會在安裝 SQL Server Data Tools (SSDT) 時一起安裝。

- [記憶體最佳化 Advisor](../../relational-databases/in-memory-oltp/memory-optimization-advisor.md)
- [下載 SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx)


#### .dacpac 檔案

您可以使用由 SSDT 管理的 .dacpac 檔案就地更新資料庫。 在 SSDT 中，您可以指定編碼在 .dacpac 檔案中的結構描述的變更。

請在類型為「資料庫」的 Visual Studio 專案內容中使用 .dacpac 檔案

- [資料層應用程式](../../relational-databases/data-tier-applications/data-tier-applications.md) 和 .dacpac 檔案



### A.4 記憶體內部 OLTP 功能是否適合您的應用程式的指引

如需記憶體內部功能是否可以改善特定應用程式效能的指引，請參閱︰

- [In-Memory OLTP (記憶體中最佳化)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)



## B. 不支援的功能

特定記憶體內部案例中不支援的功能說明於︰

- [記憶體內部 OLTP 不支援的 SQL Server 功能](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)


下列小節將強調一些更重要的不支援功能。


### B.1 資料庫快照集

在給定資料庫中第一次建立任何記憶體最佳化資料表或模組之後，無法再取得資料庫的任何[快照集](../../relational-databases/databases/database-snapshots-sql-server.md)。 特定的原因在於︰

- 第一個記憶體最佳化的項目，使得完全不可能從記憶體最佳化檔案群組卸除最後一個檔案；且
- 在記憶體最佳化檔案群組中有檔案的資料庫都無法支援快照集。

一般而言，快照集可以方便快速測試反覆運算。


### B.2 跨資料庫查詢

記憶體最佳化資料表不支援[跨資料庫](../../relational-databases/in-memory-oltp/cross-database-queries.md)的交易。 您無法在同時存取記憶體最佳化資料表的相同交易或相同查詢中存取另一個資料庫。

資料表變數並非交易式。 因此，[記憶體最佳化資料表變數](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)可用於跨資料庫查詢。


### B.3 READPAST 資料表提示

沒有查詢可以將 READPAST [資料表提示](Table%20Hints%20%28Transact-SQL%29.md)套用到任何記憶體最佳化資料表。

READPAST 提示在一些案例中很有幫助，例如數個工作階段全都存取和修改相同的少量資料列，例如在處理佇列時。


### B.4 RowVersion、Sequence

- 無法在記憶體最佳化資料表上針對 [RowVersion](../../t-sql/data-types/rowversion-transact-sql.md) 標記任何資料行。


- [SEQUENCE](../../t-sql/statements/create-sequence-transact-sql.md) 物件不能用於任何記憶體最佳化資料表。


## C. 管理維護


本節描述使用記憶體最佳化資料表時的資料庫管理差異。


### C.1 識別種子重設、遞增 > 1

[DBCC CHECKIDENT](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)，以重新植入 IDENTITY 資料行，不能用於記憶體最佳化資料表。

遞增值限制為在記憶體最佳化資料表的 IDENTITY 資料行上恰好為 1。


### C.2 DBCC CHECKDB 無法驗證記憶體最佳化資料表

[DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) 命令在其目標為記憶體最佳化資料表時，不做任何動作。 以下步驟是解決辦法︰


1. [備份交易記錄](Back%20Up%20a%20Transaction%20Log%20%28SQL Server%29.md)。

2. 將記憶體最佳化檔案群組中的檔案備份至空的裝置。 備份程序會叫用總和檢查碼驗證。

    如果找到損毀，請繼續後續步驟。

3. 將記憶體最佳化資料表的資料複製到以磁碟為基礎的資料表，進行暫時的儲存。

4. 還原記憶體最佳化檔案群組的檔案。

5. 將您暫時儲存在以磁碟為基礎的資料表中的資料 INSERT INTO (插入) 記憶體最佳化資料表。

6. DROP (卸除) 暫時保存資料的以磁碟為基礎的資料表。



## D. 效能

本節描述記憶體最佳化資料表在哪些情況下能保有優異效能的完整潛力。


### D.1 索引考量

資料表相關的陳述式 CREATE TABLE 和 ALTER TABLE 會建立和管理記憶體最佳化資料表上的所有索引。 您無法針對記憶體最佳化資料表使用 CREATE INDEX 陳述式。

當您第一次實作記憶體最佳化資料表時，傳統的 b 型樹狀目錄、非叢集索引經常是相當直覺且簡單的選擇。 稍後，在您看到應用程式的執行方式之後，可以考慮交換另一種索引類型。

兩個特殊類型的索引需要記憶體最佳化資料表的內容討論︰雜湊索引和資料行存放區索引。

如需記憶體最佳化資料表上的索引概觀，請參閱：

- [記憶體最佳化資料表的索引](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)


#### 雜湊索引

要使用 '**=**' 運算子，以精確的主索引鍵值來存取一個特定資料列時，雜湊索引可能是最快速的格式。。

- 不精確的運算子，例如 '**!=**'、'**>**'，或 '**BETWEEN**' 會損害效能，如果搭配雜湊索引使用的話。

- 如果索引鍵值重複率變得太高，則雜湊索引可能不是最佳的選擇。

- 防堵低估您的雜湊索引可能需要多少「值區」，以避免在個別值區內產生長鏈。 如需詳細資料，請參閱：
    - [記憶體最佳化資料表的雜湊索引](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md)


#### 非叢集資料行存放區索引

記憶體最佳化資料表提供一般商務交易資料的高輸送量，這個典範我們稱為「線上交易處理」或 *OLTP*。 資料行存放區索引提供彙總與類似處理的高輸送量，我們稱為「分析」。 在過去，滿足 OLTP 和分析的需求最好的方法，是使用個別的資料表，並大量移動資料，且具有某種程度的資料重複。 現在，有更簡單的**混合式解決方案**︰記憶體最佳化資料表的資料行存放區索引。


- [資料行存放區索引](Columnstore%20Indexes%20Guide.md)可以建立在以磁碟為基礎的資料表上，甚至是作為叢集索引。 但是記憶體最佳化資料表的資料行存放區索引無法加入叢集。


- 記憶體最佳化資料表的 LOB 或非資料列資料行會導致無法建立資料表的資料行存放區索引。


- 在資料表上存在資料行存放區索引時，無法對記憶體最佳化資料表執行 ALTER TABLE 陳述式。
    - 截至 2016 年 8 月，Microsoft 有短期的計劃，要改善重新建立資料行存放區索引的效能。



### D.2 LOB 和非資料列資料行

大型物件 (Lob) 是 varchar(**max**) 等類型的資料行。 在記憶體最佳化資料表上有一些 LOB 資料行，對效能的危害並不會太嚴重。 但是務必避免 LOB 資料行多於您的資料需要。 相同的建議也適用於非資料列資料行。 如果 varchar(512) 就夠了，請勿將資料行定義為 nvarchar(3072)。


一些關於 LOB 和非資料列資料行的資訊位於︰

- [記憶體最佳化資料表中的資料表和資料列大小](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)
- [記憶體中 OLTP 支援的資料類型](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md)



## E. 原生程序的限制


原生編譯的預存程序中不支援 Transact-SQL 的特定元素。

如需將 Transact-SQL 指令碼移轉至原生程序時的考量，請參閱︰

- [原生編譯預存程序的移轉問題](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)


### E.1 在原生程序中不可使用 CASE

Transact-SQL 中的 CASE 運算式不能用於原生程序內。 您可以採用的解決方法是︰

- [在原生編譯的預存程序中實作 CASE 運算式](../../relational-databases/in-memory-oltp/implementing-a-case-expression-in-a-natively-compiled-stored-procedure.md)


### E.2 在原生程序中不可使用 MERGE


Transct-SQL [MERGE 陳述式](../../t-sql/statements/merge-transact-sql.md)與一般所稱的 *upsert* 功能有相似之處。 原生程序不能使用 MERGE 陳述式。 不過，您可以使用 SELECT 加上 UPDATE 加上 INSERT 陳述式的組合，達到與 MERGE 相同的功能。 程式碼範例位於：

- [在原生編譯的預存程序中實作 MERGE 功能](../../relational-databases/in-memory-oltp/implementing-merge-functionality-in-a-natively-compiled-stored-procedure.md)



### E.3 在原生程序的 UPDATE 或 DELETE 陳述式中不可使用聯結

原生程序中的 Transact-SQL 陳述式只能存取記憶體最佳化資料表。 在 UPDATE 和 DELETE 陳述式中，您無法聯結任何資料表。 原生程序中的嘗試會失敗，並有訊例如 Msg 12319 的訊息，說明您︰

- 無法在 UPDATE 陳述式中使用 FROM 子句。
- 無法在 DELETE 陳述式中指定資料表來源。

子查詢的任何類型都未提供解決辦法。 不過，您可以使用記憶體最佳化資料表變數來達成多個陳述式的聯結結果。 兩個程式碼範例如下︰

- DELETE...JOIN...我們想要在原生程序中執行，但無法達成。
- Transact-SQL 陳述式的解決方法集，達成刪除聯結。


*案例︰*TabProjectEmployee 資料表有兩個資料行的唯一索引鍵︰ProjectId 和 EmployeeId。 每個資料列都表示員工指派到使用中專案。 當員工離職時，員工必須從 TabProjectEmployee 資料表中刪除。


#### 無效的 T-SQL, DELETE...JOIN


原生程序不能有如下的 DELETE...JOIN。


```tsql
DELETE pe
    FROM
             TabProjectEmployee   AS pe
        JOIN TabEmployee          AS e

            ON pe.EmployeeId = e.EmployeeId
    WHERE
            e.EmployeeStatus = 'Left-the-Company'
;
```


#### 有效解決辦法, 手動 DELETE...JOIN

接下來是解決辦法程式碼範例，分兩個部分︰

1. CREATE TYPE 會執行一次，在任何實際資料表變數第一次使用類型的數天前。

2. 商務程序會使用建立的類型。 一開始先宣告所建立資料表類型的資料表變數。


```tsql

CREATE TYPE dbo.type_TableVar_EmployeeId
    AS TABLE  
    (
        EmployeeId   bigint   NOT NULL
    );
```


接下來，使用建立資料表類型。


```tsql
DECLARE @MyTableVarMo  dbo.type_TableVar_EmployeeId  

INSERT INTO @MyTableVarMo (EmployeeId)
    SELECT
            e.EmployeeId
        FROM
                 TabProjectEmployee  AS pe
            JOIN TabEmployee         AS e  ON e.EmployeeId = pe.EmployeeId
        WHERE
            e.EmployeeStatus = 'Left-the-Company'
;

DECLARE @EmployeeId   bigint;

WHILE (1=1)
BEGIN
    SET @EmployeeId = NULL;

    SELECT TOP 1 @EmployeeId = v.EmployeeId
        FROM @MyTableVarMo  AS v;

    IF (NULL = @Employeed) BREAK;
    
    DELETE TabProjectEmployee
        WHERE EmployeeId = @EmployeeId;

    DELETE @MyTableVarMo
        WHERE EmployeeId = @EmployeeId;
END;
```


### E.4 原生程序的查詢計劃限制


原生程序無法使用某些類型的查詢計劃。 許多詳細資料討論於︰

- [記憶體最佳化資料表的查詢處理指南](../../relational-databases/in-memory-oltp/a-guide-to-query-processing-for-memory-optimized-tables.md)


#### 原生程序中不可使用平行處理

平行處理不能成為原生程序的任何查詢計劃的一部分。 原生程序一律為單一執行緒。


#### 聯結類型


雜湊聯結或合併聯結都不可以是原生程序的任何查詢計劃的一部分。 使用了巢狀的迴圈聯結。


#### 不可使用雜湊彙總

原生程序的查詢計劃需要彙總階段時，只能使用資料流彙總。 在原生程序序的查詢計劃中不支援雜湊彙總。

- 雜湊彙總比較適合必須彙總來自大量資料列的資料時。



## F. 應用程式設計︰交易和重試邏輯

牽涉到記憶體最佳化資料表的交易可能會依賴另一個牽涉到相同資料表的交易。 如果相依交易計數到達或超過允許的最大值，所有相依交易都會失敗。

在 SQL Server 2016 中：

- 允許的最大值是 8 個相依交易。 8 也是任何特定交易可依賴的交易數限制。
- 錯誤號碼是 41839。 (在 SQL Server 2014 中的錯誤號碼是 41301。)


您可以讓您的 Transact-SQL 指令碼更能應付可能的交易錯誤，方法是在指令碼新增「重試邏輯」。 在 UPDATE 和 DELETE 呼叫很頻繁時，或是另一個資料表中的外部索引鍵參考了記憶體最佳化的資料表時，重試邏輯更可能有幫助。 如需詳細資料，請參閱：

- [Transactions with Memory-Optimized Tables](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)
- [記憶體最佳化資料表的交易相依性限制 – 錯誤 41839](https://blogs.msdn.microsoft.com/sqlcat/2016/07/11/transaction-dependency-limits-with-memory-optimized-tables-error-41839/)



## 相關連結

- [In-Memory OLTP (記憶體中最佳化)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)

