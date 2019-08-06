---
title: SQL Graph 架構 |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, architecture
ms.assetid: ''
author: shkale-msft
ms.author: shkale
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 79a85515322d492d4356d47f78da4b79489a223e
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68811114"
---
# <a name="sql-graph-architecture"></a>SQL Graph 架構  
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

瞭解如何架構 SQL Graph。 瞭解基本概念可讓您更輕鬆地瞭解其他 SQL Graph 文章。
 
## <a name="sql-graph-database"></a>SQL Graph 資料庫
使用者可以為每個資料庫建立一個圖表。 「圖形」 (graph) 是節點和邊緣資料表的集合。 節點或邊緣資料表可以建立在資料庫的任何架構底下, 但全都屬於一個邏輯圖形。 節點資料表是類似節點類型的集合。 例如, Person 節點資料表會保存屬於圖形的所有人員節點。 同樣地, 邊緣資料表是類似類型的邊緣集合。 例如, friend edge 資料表會保存將個人連線到其他人的所有邊緣。 因為節點和邊緣是儲存在資料表中, 所以在節點或邊緣資料表上, 支援一般資料表所支援的大部分作業。 
 
 
![sql-graph-架構](../../relational-databases/graphs/media/sql-graph-architecture.png "Sql graph 資料庫架構")   

圖 1:SQL Graph 資料庫架構
 
## <a name="node-table"></a>節點資料表
節點資料表代表圖形架構中的實體。 每次建立節點資料表時, 都會建立一個隱含`$node_id`的資料行, 以唯一識別資料庫中的指定節點。 中`$node_id`的值會自動產生, 而且是該節點`object_id`資料表和內部產生的 Bigint 值的組合。 不過, 選取資料`$node_id`行時, 會顯示 JSON 字串形式的計算值。 此外, `$node_id`是虛擬資料行, 它會對應至內部名稱加上十六進位字串。 當您從`$node_id`資料表中選取時, 資料行名稱將會`$node_id_<hex_string>`顯示為。 在查詢中使用虛擬資料行名稱是查詢內部`$node_id`資料行的建議方式, 而且應該避免使用具有十六進位字串的內部名稱。

建議使用者在建立節點資料表時, 于資料`$node_id`行上建立唯一的條件約束或索引, 但如果未建立, 則會自動建立預設的唯一非叢集索引。 不過, 在基礎內部資料行上會建立圖形虛擬資料行上的任何索引。 也就是在資料`$node_id`行上建立的索引, 將會出現在內部`graph_id_<hex_string>`資料行上。   


## <a name="edge-table"></a>邊緣資料表
邊緣資料表代表圖形中的關聯性。 邊緣一律會導向並連接兩個節點。 邊緣資料表可讓使用者在圖形中建立多對多關聯性的模型。 邊緣資料表不一定有任何使用者定義的屬性。 每次建立邊緣資料表時, 都會在邊緣資料表中建立三個隱含的資料行, 以及使用者定義的屬性:

|資料行名稱    |描述  |
|---   |---  |
|`$edge_id`   |可唯一識別資料庫中的指定邊緣。 它是產生的資料行, 而值是邊緣資料表的 object_id 與內部產生的 Bigint 值的組合。 不過, 選取資料`$edge_id`行時, 會顯示 JSON 字串形式的計算值。 `$edge_id`是虛擬資料行, 其對應至具有十六進位字串的內部名稱。 當您從`$edge_id`資料表中選取時, 資料行名稱將會`$edge_id_\<hex_string>`顯示為。 在查詢中使用虛擬資料行名稱是查詢內部`$edge_id`資料行的建議方式, 而且應該避免使用具有十六進位字串的內部名稱。 |
|`$from_id`   |儲存來自邊緣來源之節點的。`$node_id`  |
|`$to_id`   |`$node_id`儲存節點的, 其為邊緣終止的位置。 |

指定邊緣可以連接的節點會受到插入`$from_id`和`$to_id`資料行中的資料所控制。 在第一版中, 您無法在邊緣資料表上定義條件約束, 以限制它能夠連接到兩種類型的節點。 也就是說, 邊緣可以連接圖形中的兩個節點, 而不論其類型為何。

與資料`$edge_id`行類似, 建議使用者在建立邊緣資料表時, 于資料行上建立唯一的索引或條件約束, 但如果未建立, 則會自動建立預設的唯一非叢集索引`$node_id`此資料行。 不過, 在基礎內部資料行上會建立圖形虛擬資料行上的任何索引。 也就是在資料`$edge_id`行上建立的索引, 將會出現在內部`graph_id_<hex_string>`資料行上。 也建議在 OLTP 案例中, 使用者會在 (`$from_id`, `$to_id`) 資料行上建立索引, 以加速在邊緣方向進行查閱。  

[圖 2] 顯示如何將節點和邊緣資料表儲存在資料庫中。 

![人員-朋友-資料表](../../relational-databases/graphs/media/person-friends-tables.png "Person 節點和朋友邊緣資料表")   

圖 2:節點和邊緣資料表標記法



## <a name="metadata"></a>中繼資料
使用這些元資料檢視來查看節點或邊緣資料表的屬性。
 
### <a name="systables"></a>sys.tables
下列新的位類型, 會將資料行新增至 SYS。多. 如果`is_node`設定為 1, 表示資料表是節點資料表, 而且如果`is_edge`設定為 1, 表示資料表是邊緣資料表。
 
|資料行名稱 |資料類型 |描述 |
|--- |---|--- |
|is_node |bit |1 = 這是節點資料表 |
|is_edge |bit |1 = 這是邊緣資料表 |
 
### <a name="syscolumns"></a>sys.columns
此`sys.columns`視圖包含額外的`graph_type`資料`graph_type_desc`行和, 表示節點和邊緣資料表中的資料行類型。
 
|資料行名稱 |資料類型 |描述 |
|--- |---|--- |
|graph_type |ssNoversion |具有一組值的內部資料行。 圖表資料行的值介於1-8 之間, 其他則為 Null。  |
|graph_type_desc |nvarchar(60)  |具有一組值的內部資料行 |
 
下表列出資料`graph_type`行的有效值

|資料行值  |描述  |
|---   |---   |
|1  |GRAPH_ID  |
|2  |GRAPH_ID_COMPUTED  |
|3  |GRAPH_FROM_ID  |
|4  |GRAPH_FROM_OBJ_ID  |
|5  |GRAPH_FROM_ID_COMPUTED  |
|6  |GRAPH_TO_ID  |
|7  |GRAPH_TO_OBJ_ID  |
|8  |GRAPH_TO_ID_COMPUTED  |


`sys.columns`也會儲存在節點或邊緣資料表中建立之隱含資料行的相關資訊。 您可以從 sys.databases 抓取下列資訊, 但使用者無法從節點或邊緣資料表中選取這些資料行。 

節點資料表中的隱含資料行

|資料行名稱    |資料類型  |is_hidden  |註解  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |內部`graph_id`資料行  |
|$node_id_\<hex_string> |NVARCHAR   |0  |外部節點`node_id`資料行  |

邊緣資料表中的隱含資料行

|資料行名稱    |資料類型  |is_hidden  |註解  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |內部`graph_id`資料行  |
|$edge_id_\<hex_string> |NVARCHAR   |0  |外部`edge_id`資料行  |
|from_obj_id_\<hex_string>  |INT    |1  |節點內部`object_id`  |
|from_id_\<hex_string>  |bigint |1  |節點內部`graph_id`  |
|$from_id_\<hex_string> |NVARCHAR   |0  |來自節點的外部`node_id`  |
|to_obj_id_\<hex_string>    |INT    |1  |節點內部`object_id`  |
|to_id_\<hex_string>    |bigint |1  |節點內部`graph_id`  |
|$to_id_\<hex_string>   |NVARCHAR   |0  |節點外部`node_id`  |
 
### <a name="system-functions"></a>系統函數
已加入下列內建函數。 這些會協助使用者從產生的資料行中解壓縮資訊。 請注意, 這些方法不會驗證使用者的輸入。 如果使用者指定了無效`sys.node_id`的, 方法會將適當的部分解壓縮, 並將其傳回。 例如, OBJECT_ID_FROM_NODE_ID 會採用`$node_id`做為輸入, 並傳回資料表的 OBJECT_ID, 此節點屬於。 
 
|內建   |描述  |
|---  |---  |
|OBJECT_ID_FROM_NODE_ID |從 object_id 解壓縮`node_id`  |
|GRAPH_ID_FROM_NODE_ID  |從 graph_id 解壓縮`node_id`  |
|NODE_ID_FROM_PARTS |從`object_id`和建立 node_id`graph_id`  |
|OBJECT_ID_FROM_EDGE_ID |解壓縮`object_id`來源`edge_id`  |
|GRAPH_ID_FROM_EDGE_ID  |從解壓縮身分識別`edge_id`  |
|EDGE_ID_FROM_PARTS |`edge_id` 從`object_id`和身分識別結構  |



## <a name="transact-sql-reference"></a>Transact-SQL 參考 
瞭解 SQL Server [!INCLUDE[tsql-md](../../includes/tsql-md.md)]和 Azure SQL Database 中引進的延伸模組, 可讓您建立及查詢圖表物件。 查詢語言延伸模組可協助使用 ASCII 藝術語法來查詢和遍歷圖表。
 
### <a name="data-definition-language-ddl-statements"></a>資料定義語言 (DDL) 語句

|工作   |相關文章  |注意
|---  |---  |---  |
|CREATE TABLE |[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-sql-graph.md)|`CREATE TABLE`現在已擴充, 可支援將資料表建立為節點或邊緣。 請注意, 邊緣資料表不一定有任何使用者定義的屬性。  |
|ALTER TABLE    |[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)|節點和邊緣資料表可以使用`ALTER TABLE`與關聯式資料表相同的方式來改變。 使用者可以加入或修改使用者定義的資料行、索引或條件約束。 不過, 修改內部圖形資料行 ( `$node_id`例如`$edge_id`或) 將會導致錯誤。  |
|CREATE INDEX   |[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  |使用者可以在節點和邊緣資料表中的虛擬資料行和使用者定義的資料行上建立索引。 支援所有索引類型, 包括叢集和非叢集資料行存放區索引。  |
|建立邊緣條件約束    |[邊緣條件&#40;約束 transact-sql&#41;](../../relational-databases/tables/graph-edge-constraints.md)  |使用者現在可以在邊緣資料表上建立邊緣條件約束, 以強制執行特定的語義, 同時維持資料完整性  |
|DROP TABLE |[DROP TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-table-transact-sql.md)  |節點和邊緣資料表可以使用`DROP TABLE`與關聯式資料表相同的方式來卸載。 不過, 在此版本中, 沒有任何條件約束可確保不會在刪除節點或節點資料表時, 不會有任何邊緣指向已刪除的節點, 也不會對邊緣進行串聯刪除。 建議您在卸載節點資料表時, 以手動方式卸載連接到該節點資料表中之節點的任何邊緣, 以維護圖形的完整性。  |


### <a name="data-manipulation-language-dml-statements"></a>資料操作語言 (DML) 語句

|工作   |相關文章  |注意
|---  |---  |---  |
|Insert |[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-sql-graph.md)|插入節點資料表與插入關聯式資料表並無不同。 [資料`$node_id`行] 的值會自動產生。 嘗試在或`$edge_id`資料行中`$node_id`插入一個值將會導致錯誤。 在插入邊緣資料表時`$from_id` , `$to_id`使用者必須提供和資料行的值。 `$from_id``$to_id` 和`$node_id`是指定邊緣連接的節點值。  |
|DELETE | [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)|節點或邊緣資料表中的資料可以從關聯式資料表中刪除的相同方式刪除。 不過, 在此版本中, 沒有任何條件約束可確保在刪除節點時不支援邊緣指向已刪除的節點, 也不會對邊緣進行串聯刪除。 建議每次刪除節點時, 也會一併刪除該節點的所有連接邊緣, 以維護圖形的完整性。  |
|UPDATE |[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  |使用者定義資料行中的值可以使用 UPDATE 語句來更新。 不允許更新內部圖形資料`$node_id`行`$edge_id`、 `$from_id` 、 `$to_id`和。  |
|MERGE |[MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  |`MERGE`節點或邊緣資料表支援語句。  |


### <a name="query-statements"></a>查詢語句

|工作   |相關文章  |注意
|---  |---  |---  |
|SELECT |[SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)|節點和邊緣會在內部儲存為數據表, 因此在 SQL Server 或 Azure SQL Database 的資料表上支援的大部分作業, 在節點和邊緣資料表上都支援。  |
|MATCH  | [MATCH &#40;Transact-SQL&#41;](../../t-sql/queries/match-sql-graph.md)|會引進符合內建的, 以支援模式比對和透過圖形進行遍歷。  |



## <a name="limitations-and-known-issues"></a>限制與已知問題  
在此版本中, 節點和邊緣資料表有某些限制:
* 本機或全域臨時表不可以是節點或邊緣資料表。
* 資料表類型和資料表變數不能宣告為節點或邊緣資料表。 
* 無法將節點和邊緣資料表建立為系統設定版本的時態表。   
* 節點和邊緣資料表不可以是記憶體優化資料表。  
* 使用者無法使用 update `$from_id`語句`$to_id`來更新邊緣的和資料行。 若要更新邊緣連接的節點, 使用者必須插入指向新節點的新邊緣, 並刪除上一個節點。
* 不支援繪圖物件上的跨資料庫查詢。 


## <a name="next-steps"></a>後續步驟
若要開始使用新的語法, 請參閱[SQL Graph 資料庫-範例](./sql-graph-sample.md)
 

