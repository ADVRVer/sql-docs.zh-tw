---
title: "MSSQL_REPL027183 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL027183 錯誤"
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027183
    
## 訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|27183|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|合併處理無法以參數化資料列篩選器來列舉發行項的變更。 如果這個失敗繼續發生，請增加這個處理的查詢逾時、縮短發行集的保留期限，以及改善發行資料表的索引。|  
  
## 說明  
 如果在已篩選發行集中處理變更時發生「合併代理程式」逾時，則會出現此錯誤。 逾時可能是由下列問題其中之一造成：  
  
-   未使用預先計算分割區最佳化。  
  
-   資料行上索引片段已用於篩選。  
  
-   大型合併中繼資料表，例如 **MSmerge_tombstone**, ，**MSmerge_contents**, ，和 **MSmerge_genhistory**。  
  
-   已篩選資料表未聯結在唯一索引鍵上，並且聯結包含大量資料表的篩選。  
  
## 使用者動作  
 若要解決這個問題：  
  
-   增加的值， **-QueryTimeOut** 參數合併代理程式以便處理繼續進行，同時您在解決基礎問題造成此錯誤。 可於代理程式設定檔和命令列中指定代理程式參數。 如需詳細資訊，請參閱：  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [檢視及修改複寫代理程式命令提示字元參數 & #40。SQL Server Management Studio & #41;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [複寫代理程式可執行檔概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)。  
  
-   儘可能使用預先計算分割區最佳化。 如果符合一些發行集需求，則依預設使用此最佳化。 如需這些需求的詳細資訊，請參閱 [最佳化 Parameterized Filter Performance with Precomputed Partitions](../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)。 如果發行集不符合這些需求，則請考慮重新設計此發行集。  
  
-   為發行集保留期限指定可能的最低設定，因為只有在達到保留期限時，複寫才可以清除發行集與訂閱資料庫中的中繼資料。 如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)。  
  
-   合併式複寫維護的一部分，偶爾會檢查與合併式複寫相關的系統資料表的成長︰ **MSmerge_contents**, ，**MSmerge_genhistory**, ，和 **MSmerge_tombstone**, ，**MSmerge_current_partition_mappings**, ，和 **MSmerge_past_partition_mappings**。 定期重新整理資料表的索引。 如需詳細資訊，請參閱 [重新組織與重建索引](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)。  
  
-   確定用於篩選的資料行索引正確，並在需要時重建這些索引。 如需詳細資訊，請參閱 [重新組織與重建索引](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)。  
  
-   設定 **join_unique_key** 唯一的資料行為基礎的聯結篩選的屬性。 如需相關資訊，請參閱 [Join Filters](../../relational-databases/replication/merge/join-filters.md)。  
  
-   限制聯結篩選階層中資料表的數量。 若您正在產生五個以上資料表的聯結篩選，請考慮其他方案：不要篩選小型、無法變更或主要為查詢資料表的資料表。 聯結篩選只能用於必須在訂閱中分割的資料表之間。  
  
-   在同步處理之間少量變更已篩選的資料表，或更頻繁地執行「合併代理程式」。 如需設定同步排程的詳細資訊，請參閱 [指定同步處理排程](../../relational-databases/replication/specify-synchronization-schedules.md)。  
  
## 另請參閱  
 [錯誤和事件參考 & #40。複寫 & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  