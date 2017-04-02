---
title: "清除合併中繼資料 (複寫 Transact-SQL 程式設計) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "中繼資料 [SQL Server 複寫]"
  - "sp_mergemetadataretentioncleanup"
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# 清除合併中繼資料 (複寫 Transact-SQL 程式設計)
  合併式複寫中繼資料會由「合併代理程式」依據發行集的保留設定而定期清除。 這會出現在 「 發行者 」 與 「 訂閱者 」 [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), ，[MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), ，[MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), ，[MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md), ，和 [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) 系統資料表。 您也可以使用複寫預存程序，以程式設計方式清除這些資料表中的資料。  
  
### 若要手動清除合併中繼資料  
  
1.  在發行集資料庫的發行者，執行 [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md)。  
  
2.  （選擇性）請注意在中移除的資料列數目步驟 1 中的從 [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), ，[MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), ，和 [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) 系統資料表，傳回分別以 **@num_genhistory_rows**, ，**@num_contents_rows**, ，和 **@num_tombstone_rows** 輸出參數。  
  
3.  在「訂閱者」端重複步驟 1 和 2，以清除訂閱者資料庫上的中繼資料。  
  
## 另請參閱  
 [訂閱逾期與停用](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  