---
title: "基數估計 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b1c53b09fe118de3a90c78bd1393da90a915385b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="cardinality-estimation-sql-server"></a>基數估計 (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  
本文描述如何評估及選擇最適合您的 SQL 系統的基數估計 (CE) 組態。 大多數系統皆可從最新的 CE 中受益，因為它的精確度最高。 CE 會預測您的查詢可能傳回的資料列數目。 查詢最佳化工具使用基數預測，來產生最佳查詢計劃。 由於估計較精確，因此查詢最佳化工具通常較有機會產生較佳的查詢計劃。  
  
您的應用程式系統可能有項重要的查詢，其計劃因此新的 CE 而變更為速度較慢的計劃。 這類查詢可能類似下列其中一項：  
  
- 執行頻繁很高而經常同時執行多個執行個體的 OLTP (線上交易處理) 查詢。  
- 在您的 OLTP 營業期間執行大量彙總的 SELECT。  
  
您有幾個方法來指出使用新的 CE 執行較慢的查詢。 您也可以選擇要如何解決此效能問題。  
  
  
## <a name="versions-of-the-ce"></a>CE 的版本  
  
 1998 年，Microsoft SQL Server 7.0 隨附提供 CE 的一項重大更新，其相容性層級為 70。 後續更新從 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 開始，表示相容性層級為 120 及以上。 層級 120 及以上的 CE 更新併入假設和演算法，適用於新式資料倉儲和 OLTP 工作負載。  
  
 **相容性層級** ︰您可以使用下列有關 [COMPATIBILITY_LEVEL](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)的 Transact-SQL 程式碼，來確保您的資料庫處於特定層級。  

```tsql  
SELECT ServerProperty('ProductVersion');  
go  
  
ALTER DATABASE <yourDatabase>  
    SET COMPATIBILITY_LEVEL = 130;  
go  
  
SELECT d.name, d.compatibility_level  
    FROM sys.databases AS d  
    WHERE d.name = 'yourDatabase';  
go  
```  
  
 若是相容性層級設定為 120 或以上的 SQL Server 資料庫，啟用[追蹤旗標 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 會強制系統使用 CE 版本 70。  
  
 **舊版 CE：**若是相容性層級設定為 120 以上的 SQL Server 資料庫，可使用 [ALTER DATABASE SCOPED CONFIGURATION](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) 在資料庫層級啟用 CE 版本 70。
  
```tsql  
ALTER DATABASE
    SCOPED CONFIGURATION  
        SET LEGACY_CARDINALITY_ESTIMATION = ON;  
go  
  
SELECT name, value  
    FROM sys.database_scoped_configurations  
    WHERE name = 'LEGACY_CARDINALITY_ESTIMATION';  
```  
 
 或者從 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 開始，使用[查詢提示](../../t-sql/queries/hints-transact-sql-query.md) `USE HINT ('FORCE_LEGACY_CARDINALITY_ESTIMATION')`。
 
 ```tsql  
SELECT CustomerId, OrderAddedDate  
    FROM OrderTable  
    WHERE OrderAddedDate >= '2016-05-01'; 
    OPTION (USE HINT ('FORCE_LEGACY_CARDINALITY_ESTIMATION'));  
```
 
 **查詢存放區**︰從 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 開始，提供查詢存放區工具，方便您檢查查詢的效能。 在 [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] 中，啟用查詢存放區的情況下，**物件總管**中的資料庫節點下會顯示**查詢存放區**節點。  
  
```tsql  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE = ON;  
go  
  
SELECT  
        q.actual_state_desc AS [actual_state_desc-ofQueryStore],  
        q.desired_state_desc,  
        q.query_capture_mode_desc  
    FROM  
        sys.database_query_store_options  AS q;  
go  
  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE CLEAR;  
```  
  
 > [!TIP] 
 > 建議您安裝最新版本的 [Management Studio](http://msdn.microsoft.com/library/mt238290.aspx)，並經常進行更新。  
  
 追蹤基數估計處理序的另一個做法，是使用名為 **query_optimizer_estimate_cardinality** 的擴充事件。 下列 T-SQL 程式碼範例會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上執行。 它會將 .xel 檔案寫入 C:\Temp\ (不過您可以變更此路徑)。 當您在 [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] 中開啟 .xel 檔案時，會以使用方便的方式來顯示其詳細資訊。  
  
```tsql  
DROP EVENT SESSION Test_the_CE_qoec_1 ON SERVER;  
go  
  
CREATE EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    ADD EVENT sqlserver.query_optimizer_estimate_cardinality  
    (  
        ACTION (sqlserver.sql_text)  
            WHERE (  
                sql_text LIKE '%yourTable%'  
                and sql_text LIKE '%SUM(%'  
            )  
    )  
    ADD TARGET package0.asynchronous_file_target   
        (SET  
            filename = 'c:\temp\xe_qoec_1.xel',  
            metadatafile = 'c:\temp\xe_qoec_1.xem'  
        );  
go  
  
ALTER EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    STATE = START;  --STOP;  
go  
```  
  
 如需為 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 量身訂做之擴充事件的相關資訊，請參閱 [SQL Database 中的擴充事件](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)。  
  
  
## <a name="steps-to-assess-the-ce-version"></a>評估 CE 版本的步驟  
  
 接下來的步驟可讓您用來評估是否有任何最重要查詢在最新 CE 下的執行效能不佳。 其中一些步驟是透過執行上一節所示的程式碼範例來進行。  
  
1.  開啟 [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]。 確定您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫已設定為最高可用的相容性層級。  
  
2.  執行下列預備步驟：  
  
    1.  開啟 [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]。  
  
    2.  執行 T-SQL，確定您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫已設定為最高可用的相容性層級。  
  
    3.  確定您的資料庫已關閉其 `LEGACY_CARDINALITY_ESTIMATION` 組態。  
  
    4.  「清除」您的查詢存放區。 當然，請確定您的查詢存放區處於開啟狀態。  
  
    5.  執行陳述式：`SET NOCOUNT OFF;`  
  
3.  執行陳述式：`SET STATISTICS XML ON;`  
  
4.  執行您的重要查詢。  
  
5.  記下結果窗格中 [訊息] 索引標籤上實際受影響的資料列數目。  
  
6.  在結果窗格的 [結果] 索引標籤上，按兩下包含 XML 格式統計資料的資料格。 圖形查詢計劃隨即顯示。  
  
7.  以滑鼠右鍵按一下圖形查詢計劃中的第一個方塊，然後按一下 [屬性]。  
  
8.  為了在稍後比較不同的組態，請記下下列屬性的值：  
  
    -   [CardinalityEstimationModelVersion]。  
  
    -   [估計的資料列數目]。  
  
    -   [估計的 I/O 成本]，以及涉及實際效能 (而不是資料列計數預測) 的幾個類似 [估計] 屬性。  
  
    -   [邏輯作業] 和 [實體作業]。 [平行處理原則] 是正確值。  
  
    -   [實際的執行模式]。 [批次] 是正確值，優於 [資料列]。  
  
9. 比較估計的資料列數目與實際的資料列數目。 CE 誤差是 1% (高或低)，或是 10%？  
  
10. 執行：`SET STATISTICS XML OFF;`  
  
11. 執行 T-SQL 將您的資料庫相容性層級降低一個層級 (例如從 130 降低到 120)。  
  
12. 重新執行所有非預備步驟。  
  
13. 比較兩次執行的 CE 屬性值。  
  
    - 最新 CE 的誤差百分比是否小於舊版 CE？  
  
14. 最後，比較這兩次執行的各種效能屬性值。  
  
    -   您的查詢是否在這兩個不同的 CE 估計下使用不同的計劃？  
  
    -   您的查詢在最新的 CE 下是否執行得較慢？  
  
    -   除非您的查詢在舊版 CE 下的執行效果更佳且使用不同的計劃，否則幾乎可以確定您需要最新的 CE。  
  
    -   不過，如果您的查詢在舊版 CE 下執行更快速的計劃，請考慮強制系統使用更快速的計劃並忽略此 CE。 如此一來，您不但可以針對所有項目使用最新的 CE，同時也可以在偶爾的情況下保留更快速的計劃。  
  
## <a name="how-to-activate-the-best-query-plan"></a>如何啟用最佳查詢計劃  
  
假設使用新的 CE 會為您的查詢產生速度較慢的查詢計劃。 以下是啟用更快速的計劃的一些選項。  
  
您可以將整個資料庫的相容性層級設定成比最新可用的值更低。  
  
- 這樣會啟用舊版 CE，但會使得所有查詢受限於舊版且較不精確的 CE。  
  
- 此外，舊版相容性層級也會失去查詢最佳化工具的絕佳改善。  
  
您可以使用 `LEGACY_CARDINALITY_ESTIMATION` 讓整個資料庫使用舊版 CE，或只使用特定查詢，同時保留查詢最佳化工具的改善。  
  
若要進行最精細的控制，您可以「強制」SQL 系統在測試期間使用透過舊版 CE 所產生的計劃。 「固定」您慣用的計劃之後，您可以將整個資料庫設定為使用最新的相容性層級和 CE。 接下來將會詳細說明這個選項。  
  
### <a name="how-to-force-a-particular-query-plan"></a>如何強制執行特定查詢計劃  
  
查詢存放區提供不同的方式，讓您強制系統使用特定查詢計劃：  
  
- 執行 **sp_query_store_force_plan**。  
  
- 在 [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] 中，展開您的 [查詢存放區] 節點，以滑鼠右鍵按一下 [Top Resource Consuming Nodes] (資源耗用量排名在前的節點)，然後按一下 [View Top Resource Consuming Nodes] (檢視資源耗用量排名在前的節點)。 這會顯示標示為 **[強制執行計畫]** 和 **[取消強制執行計畫]** 的按鈕。  
  
 如需查詢存放區的詳細資訊，請參閱 [使用查詢存放區監視效能](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)。  
  
  
## <a name="examples-of-ce-improvements"></a>CE 改善範例  
  
本節描述因實作最新版 CE 的增強功能而受益的範例查詢。 這是背景資訊，不需要您執行特定動作。  
  
### <a name="example-a-ce-understands-maximum-value-might-be-higher-than-when-statistics-were-last-gathered"></a>範例 A：CE 認為最大值可能比上次收集統計資料時還要高  
  
假設上次是在 2016 年 4 月 30 日收集 OrderTable 的統計資料，而最大 OrderAddedDate 是 2016 年 4 月 30 日。 相容性層級 120 (及更高層級) 的 CE 認為 OrderTable 中資料行所包含之「遞增」資料的值，可能大於統計資料所記錄的最大值。 此認知改進了類似如下之 SQL SELECT 的查詢計劃。  
  
```tsql  
SELECT CustomerId, OrderAddedDate  
    FROM OrderTable  
    WHERE OrderAddedDate >= '2016-05-01';  
```  
  
### <a name="example-b-ce-understands-that-filtered-predicates-on-the-same-table-are-often-correlated"></a>範例 B：CE 認為相同資料表上的篩選述詞通常相互關聯  
  
在下列 SELECT 中，我們看到 Model 和 ModelVariant 的篩選述詞。 我們直覺認為當 Model 為 'Xbox' 時，ModelVariant 有可能為 'One' (有鑑於 Xbox 有一個名為 One 的變數)。  
  
層級 120 的 CE 認為相同資料表上的兩個資料行 Model 和 ModelVariant 之間可能會相互關聯。 CE 可更準確地的估計查詢所要傳回的資料列數目，而且查詢最佳化工具會產生更佳的計劃。  
  
```tsql  
SELECT Model, Purchase_Price  
    FROM dbo.Hardware  
    WHERE  
        Model  = 'Xbox'  AND  
        ModelVariant = 'One';  
```  
  
### <a name="example-c-ce-no-longer-assumes-any-correlation-between-filtered-predicates-from-different-tablescc"></a>範例 C：CE 不會再假設來自不同資料表的篩選述詞之間有任何相互關聯 
對新式工作負載和實際商務資料的最新詳細研究顯示，來自不同資料表的述詞篩選條件通常彼此沒有關聯。 在下列查詢中，CE 假設 s.type 和 r.date 之間沒有關聯。 因此，CE 所估計的傳回資料列數目比較低。  
  
```tsql  
SELECT s.ticket, s.customer, r.store  
    FROM  
                   dbo.Sales    AS s  
        CROSS JOIN dbo.Returns  AS r  
    WHERE  
        s.ticket = r.ticket  AND  
        s.type   = 'toy'     AND  
        r.date   = '2016-05-11';  
```  
  
  
## <a name="see-also"></a>另請參閱  
 [效能的監視與微調](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator](http://msdn.microsoft.com/library/dn673537.aspx) (使用 SQL Server 2014 基數估算程式最佳化您的查詢計劃)  
 [查詢提示](../../t-sql/queries/hints-transact-sql-query.md)  
 [使用查詢存放區監視效能](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
 [查詢處理架構指南](../../relational-databases/query-processing-architecture-guide.md)
