---
title: "DBCC SHOW_STATISTICS (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 12/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHOW_STATISTICS_TSQL
- DBCC SHOW_STATISTICS
- SHOW_STATISTICS
- DBCC_SHOW_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query optimization statistics [SQL Server], densities
- histograms [SQL Server]
- statistical information [SQL Server], viewing statistics objects
- current distribution statistics
- query optimization statistics [SQL Server], histograms
- DBCC SHOW_STATISTICS statement
- distribution statistics
- statistical information [SQL Server], densities
- statistics objects
- statistical information [SQL Server], histograms
- query optimization statistics [SQL Server], viewing statistics objects
- statistical information [SQL Server], distribution
- densities [SQL Server]
- displaying distribution statistics
ms.assetid: 12be2923-7289-4150-b497-f17e76a50b2e
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: 66f00526254a3592c3bb980ecf22c390b88cb687
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-showstatistics-transact-sql"></a>DBCC SHOW_STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

DBCC SHOW_STATISTICS 會針對資料表或索引檢視表顯示目前的查詢最佳化統計資料。 查詢最佳化工具會使用統計資料來預估基數或查詢結果中的資料列數，如此可讓查詢最佳化工具建立高品質的查詢計畫。 例如，查詢最佳化工具可使用基數預估來選擇查詢計畫中的索引搜尋運算子，而不是索引掃描運算子，避免發生資源密集的索引掃描來提高查詢效能。
  
查詢最佳化工具會將資料表或索引檢視表的統計資料儲存在統計資料物件中。 如果是資料表，將會在索引或資料表資料行清單上建立統計資料物件。 統計資料物件包含標頭 (其中包含有關統計資料的中繼資料)、長條圖 (包含統計資料物件之第一個索引鍵資料行中的值分佈)，以及用來測量跨資料行關聯的密度向量。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 可以使用統計資料物件中的任何資料來計算基數預估。
  
DBCC SHOW_STATISTICS 會根據儲存在統計資料物件中的資料來顯示標頭、長條圖和密度向量。 此語法可讓您指定資料表或索引檢視表，連同目標索引名稱、統計資料名稱或資料行名稱。 此主題描述如何顯示統計資料以及如何了解顯示的結果。
  
如需詳細資訊，請參閱 [Statistics](../../relational-databases/statistics/statistics.md)。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```
-- Syntax for SQL Server and Azure SQL Database  
  
DBCC SHOW_STATISTICS ( table_or_indexed_view_name , target )   
[ WITH [ NO_INFOMSGS ] < option > [ , n ] ]  
< option > :: =  
    STAT_HEADER | DENSITY_VECTOR | HISTOGRAM | STATS_STREAM  
```  
  
```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

DBCC SHOW_STATISTICS ( table_name , target )   
    [ WITH {STAT_HEADER | DENSITY_VECTOR | HISTOGRAM } [ ,...n ] ]  
[;]  
```  
  
## <a name="arguments"></a>引數  
 *table_or_indexed_view_name*  
 要顯示統計資料資訊之資料表或索引檢視表的名稱。  
  
 *table_name*  
 包含要顯示的統計資料的資料表名稱。 資料表不能為外部資料表。  
  
 *目標*  
 要顯示統計資料資訊之索引、統計資料或資料行的名稱。 *目標*括在括號，單一引號、 double 引號括住或沒有引號。 如果*目標*是現有索引的名稱，或傳回資料表或索引檢視表，此目標的統計資料資訊的統計資料。 如果*目標*是現有的資料行的名稱，且此資料行上的自動建立統計資料存在，則會傳回該自動建立統計資料的相關資訊。 如果資料行目標之自動建立的統計資料不存在，就會傳回錯誤訊息 2767。  
 在[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，*目標*不可以是資料行名稱。  
  
 NO_INFOMSGS  
 抑制所有嚴重性層級在 0 到 10 的參考用訊息。  
  
 STAT_HEADER |DENSITY_VECTOR |長條圖 |STATS_STREAM [**，* * * n* ]  
 如果指定其中一或多個選項，就會限制陳述式針對指定之選項所傳回的結果集。 如果沒有指定任何選項，便會傳回所有的統計資料資訊。  
  
 STATS_STREAM 是 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>結果集  
下表描述指定 STAT_HEADER 時，結果集所傳回的資料行。
  
|資料行名稱|Description|  
|-----------------|-----------------|  
|名稱|統計資料物件的名稱。|  
|已更新|上次更新統計資料的日期和時間。 [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md)函式會擷取這項資訊的替代方式。 如需詳細資訊，請參閱[備註](#Remarks)此頁面中的區段。|  
|資料列|上一次更新統計資料時位於資料表或索引檢視表中的資料列總數。 如果篩選了統計資料或是統計資料對應至篩選過的索引，此資料列數可能會少於資料表中的資料列數。 如需詳細資訊，請參閱[統計資料](../../relational-databases/statistics/statistics.md)。|  
|取樣的資料列|針對統計資料計算進行取樣的資料列總數。 如果取樣的資料列數 < 資料列數，顯示的長條圖和密度結果將會是根據取樣資料列數的預估值。|  
|步驟|長條圖中的步驟數。 每一個步驟都會跨越某個範圍的資料行值，後面緊接著上限資料行值。 長條圖步驟會在統計資料中的第一個索引鍵資料行上定義。 步驟數的最大值為 200。|  
|密度|針對統計資料物件第一個索引鍵資料行中的所有值，計算為 1 / 相異值，不包括長條圖界限值。 查詢最佳化工具不會使用這個 Density 值，而且會針對與 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 之前版本之間的回溯相容性顯示。|  
|平均索引鍵長度|針對統計資料物件中的所有索引鍵資料行計算之每個值的平均位元組數。|  
|String Index|Yes 表示統計資料物件包含了字串摘要統計資料來改善使用 LIKE 運算子之查詢述詞的基數預估，例如 `WHERE ProductName LIKE '%Bike'`。 字串摘要統計資料會與長條圖分開儲存，並為類型時建立的統計資料物件第一個索引鍵資料行**char**， **varchar**， **nchar**， **nvarchar**， **varchar （max)**， **nvarchar （max)**，**文字**，或**ntext。**。|  
|篩選運算式|包含在統計資料物件中之資料表資料列子集的述詞。 NULL = 非篩選的統計資料。 如需有關篩選述詞的詳細資訊，請參閱[Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)。 如需篩選的統計資料的詳細資訊，請參閱[統計資料](../../relational-databases/statistics/statistics.md)。|  
|Unfiltered Rows|套用篩選運算式之前，資料表中的資料列總數。 如果 Filter Expression 為 NULL，Unfiltered Rows 就會等於 Rows。|  
|保存範例百分比|保存未明確指定取樣百分比的統計資料更新所使用的取樣百分比。 如果值為零，這個統計資料的設定沒有持續性的範例百分比。<br /><br /> **適用於：** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4| 
  
下表描述指定 DENSITY_VECTOR 時，結果集所傳回的資料行。
  
|資料行名稱|Description|  
|-----------------|-----------------|  
|所有密度|密度是 1 / 相異值。 結果會針對統計資料物件中資料行的每個前置詞來顯示密度，一個密度一個資料列。 相異值是每個資料列和每個資料行前置詞的資料行值相異清單。 例如，如果統計資料物件包含索引鍵資料行 (A, B, C)，結果就會報告每一個資料行前置詞中相異值清單的密度：(A)、(A,B) 和 (A, B, C)。 使用前置詞 (A, B, C) 時，這些清單的每一個都會是相異值清單：(3, 5, 6)、(4, 4, 6)、(4, 5, 6)、(4, 5, 7)。 使用前置詞 (A, B) 時，相同的資料行值都會有這些相異值清單：(3, 5)、(4, 4) 和 (4, 5)。|  
|平均長度|平均長度 (以位元組為單位)，用來儲存資料行前置詞的資料行值清單。 例如，如果清單 (3, 5, 6) 中的每一個值都需要 4 位元組，長度就是 12 位元組。|  
|資料行|在前置詞中顯示 All density 和 Average length 的資料行名稱。|  
  
下表描述指定 HISTOGRAM 選項時，結果集所傳回的資料行。
  
|資料行名稱|Description|  
|---|---|
|RANGE_HI_KEY|長條圖步驟的上限資料行值。 此資料行值也稱為索引鍵值。|  
|RANGE_ROWS|資料行值在長條圖步驟內的預估資料列數，不包括上限。|  
|EQ_ROWS|資料行值等於長條圖步驟之上限的預估資料列數。|  
|DISTINCT_RANGE_ROWS|在長條圖步驟內具有相異資料行值的預估資料列數，不包括上限。|  
|AVG_RANGE_ROWS|在長條圖步驟內具有重複資料行值的平均資料列數，上限不包括在內 (RANGE_ROWS / DISTINCT_RANGE_ROWS for DISTINCT_RANGE_ROWS > 0)。| 
  
## <a name="Remarks"></a> 備註 

統計資料更新將日期儲存在[統計資料的 blob 物件](../../relational-databases/statistics/statistics.md#DefinitionQOStatistics)搭配[長條圖](#histogram)和[密度向量](#density)、 中繼資料中找不到。 讀取任何資料時產生統計資料，就不會建立統計資料的 blob，日期無法使用，而*更新*資料行是 NULL。 這是篩選的統計資料述詞未傳回任何資料列，或新的空白資料表的情況。
  
## <a name="histogram"></a> 長條圖  
長條圖會測量資料集中每一個相異值的發生頻率。 查詢最佳化工具會計算有關統計資料物件之第一個索引鍵資料行中資料行值的長條圖，以統計方式取樣資料列或執行資料表或檢視表中所有資料列的完整掃描來選取資料行值。 如果長條圖是從一組取樣的資料列所建立，資料列數和相異值數的儲存總計會是預估值，而且不需要為整數。
  
若要建立長條圖，查詢最佳化工具會排序資料行值、計算符合每一個相異資料行值的值數目，然後將資料行值彙總成最多 200 個連續長條圖步驟。 每一個步驟都包含某個範圍的資料行值，後面緊接著上限資料行值。 此範圍包括界限值之間的所有可能資料行值，但是不包括界限值本身。 最低的已排序資料行值就是第一個長條圖步驟的上限值。
  
下列長條圖顯示包含六個步驟的長條圖。 第一個上限值左側的區域就是第一個步驟。
  
![](../../relational-databases/system-dynamic-management-views/media/a0ce6714-01f4-4943-a083-8cbd2d6f617a.gif "a0ce6714-01f4-4943-a083-8cbd2d6f617a")
  
每一個長條圖步驟：
-   粗線代表上限值 (RANGE_HI_KEY) 以及其所發生的次數 (EQ_ROWS)  
-   RANGE_HI_KEY 左邊的實線區域代表資料行值範圍以及每一個資料行值發生的平均次數 (AVG_RANGE_ROWS)。 第一個長條圖步驟的 AVG_RANGE_ROWS 一定是 0。  
-   虛線代表用來預估範圍內相異值總數的取樣值 (DISTINCT_RANGE_ROWS) 以及範圍內的值總數 (RANGE_ROWS)。 查詢最佳化工具會使用 RANGE_ROWS 和 DISTINCT_RANGE_ROWS 來計算 AVG_RANGE_ROWS，而且不會儲存取樣值。  
  
查詢最佳化工具會根據長條圖步驟的統計重要性來定義長條圖步驟。 它會使用最大值差異演算法，讓長條圖中的步驟數減至最少，同時讓界限值之間的差異最大化。 步驟數的最大值為 200。 長條圖步驟的數目可以少於相異值數目，即使包含了少於 200 個界限點的資料行也是如此。 例如，包含 100 個相異值的資料行可以擁有少於 100 個界限點的長條圖。
  
## <a name="density"></a> 密度向量  
查詢最佳化工具會使用密度來增強查詢的基數預估，這些查詢會從相同的資料表或索引檢視表傳回多個資料行。 密度向量針對統計資料物件中資料行的每個前置詞各包含一個密度。 例如，如果統計資料物件具有 `CustomerId`、`ItemId` 和 `Price` 等索引鍵資料行，就會根據下列每一個資料行前置詞來計算密度。
  
|資料行前置詞|計算密度的依據|  
|---|---|
|(CustomerId)|與 CustomerId 的值相符的資料列|  
|(CustomerId, ItemId)|與 CustomerId 和 ItemId 的值相符的資料列|  
|(CustomerId, ItemId, Price)|與 CustomerId、ItemId 和 Price 的值相符的資料列|  
  
## <a name="restrictions"></a>限制  
 DBCC SHOW_STATISTICS 不會提供空間或 xVelocity 記憶體最佳化的資料行存放區索引之統計資料。  
  
## <a name="permissions-for-includessnoversionincludesssnoversion-mdmd-and-includesssdsincludessssds-mdmd"></a>權限[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]和[!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
才能檢視統計資料物件，使用者必須擁有資料表，或者使用者必須是成員`sysadmin`固定伺服器角色、`db_owner`固定資料庫角色或`db_ddladmin`固定的資料庫角色。
  
[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]SP1 會修改權限限制，並允許具有 SELECT 權限，才能使用這個命令的使用者。 請注意，必須先符合下列需求，足夠的 SELECT 權限才能執行此命令：
-   使用者必須有統計資料物件的所有資料行的權限  
-   使用者必須有篩選條件 (如果有) 的所有資料行的權限  
-   資料表不能有資料列層級安全性原則。  
  
若要停用此行為，請使用追蹤旗標 9485。
  
## <a name="permissions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>權限[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC SHOW_STATISTICS 需要 SELECT 權限表格或下列其中之一的成員資格：
-   sysadmin 固定伺服器角色  
-   db_owner 固定的資料庫角色  
-   db_ddladmin 固定的資料庫角色  
  
## <a name="limitations-and-restrictions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>限制的事項[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC SHOW_STATISTICS 會顯示在控制項節點層級的 Shell 資料庫中儲存的統計資料。 不會顯示所自動建立的統計資料[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]計算節點上。
  
外部資料表不支援 DBCC SHOW_STATISTICS。
  
## <a name="examples-includessnoversionincludesssnoversion-mdmd-and-includesssdsincludessssds-mdmd"></a>範例：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]和[!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
### <a name="a-returning-all-statistics-information"></a>A. 傳回所有的統計資料資訊  
下列範例會顯示所有的統計資料資訊，包括`AK_Address_rowguid`索引`Person.Address`資料表中[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]資料庫。
  
```sql
DBCC SHOW_STATISTICS ("Person.Address", AK_Address_rowguid);  
GO  
```  
  
### <a name="b-specifying-the-histogram-option"></a>B. 指定 HISTOGRAM 選項  
這會限制針對 Customer_LastName 顯示長條圖資料的統計資料資訊。
  
```sql
DBCC SHOW_STATISTICS ("dbo.DimCustomer",Customer_LastName) WITH HISTOGRAM;  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="c-display-the-contents-of-one-statistics-object"></a>C. 顯示一個統計資料物件的內容  
 下列範例會顯示 DimCustomer 資料表上 Customer_LastName 統計資料的內容。  
  
```sql
-- Uses AdventureWorks  
--First, create a statistics object  
CREATE STATISTICS Customer_LastName   
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName);  
GO  
DBCC SHOW_STATISTICS ("dbo.DimCustomer",Customer_LastName);  
GO  
```  
  
結果會顯示標頭、 密度向量和長條圖的一部分。
  
![DBCC SHOW_STATISTICS 結果](../../t-sql/database-console-commands/media/aps-sql-dbccshow-statistics.JPG "DBCC SHOW_STATISTICS 結果")
  
## <a name="see-also"></a>另請參閱  
[統計資料](../../relational-databases/statistics/statistics.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
[CREATE STATISTICS &#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)  
[DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)  
[sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)  
[sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)  
[STATS_DATE &#40;Transact-SQL&#41;](../../t-sql/functions/stats-date-transact-sql.md)  
[UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
[sys.dm_db_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)  
[sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md)   
