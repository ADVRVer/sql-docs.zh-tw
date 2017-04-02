---
title: "卸除資料庫快照集 (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "移除資料庫快照集"
  - "刪除資料庫快照集"
  - "資料庫快照集 [SQL Server], 刪除"
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
caps.latest.revision: 36
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# 卸除資料庫快照集 (Transact-SQL)
  卸除資料庫快照集，就會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 刪除資料庫快照集，並刪除快照集所使用的疏鬆檔案。 卸除資料庫快照集後，快照集的所有使用者連接都會結束。  
  
## 安全性  
  
###  <a name="Permissions"></a> Permissions  
 具有 DROP DATABASE 權限的任何使用者都可以卸除資料庫快照集。  
  
##  <a name="TsqlProcedure"></a> 如何卸除資料庫快照集 (使用 Transact-SQL)  
 **若要卸除資料庫快照集**  
  
1.  識別您想要卸除的資料庫快照集。 您可以檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中之資料庫的快照集。 如需詳細資訊，請參閱[檢視資料庫快照集 &#40;SQL Server&#41;](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)。  
  
2.  發出 [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md) 陳述式，並指定所要卸除之資料庫快照集的名稱。 其語法如下：  
  
     DROP DATABASE *database_snapshot_name* [ **,**...*n* ]  
  
     其中，*database_snapshot_name* 是所要卸除之資料庫快照集的名稱。  
  
####  <a name="TsqlExample"></a> 範例 (Transact-SQL)  
 下列範例會卸除名為 SalesSnapshot0600 的資料庫快照集，而不會影響來源資料庫。  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 SalesSnapshot0600 的任何使用者連接都會結束，而且快照集所使用的所有 NTFS 檔案系統疏鬆檔案也都會被刪除。  
  
> [!NOTE]  
>  如需資料庫快照集使用疏鬆檔案的相關資訊，請參閱[資料庫快照集 &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)。  
  
##  <a name="RelatedTasks"></a> 相關工作  
  
-   [建立資料庫快照集 &#40;Transact-SQL&#41;](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [檢視資料庫快照集 &#40;SQL Server&#41;](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [將資料庫還原成資料庫快照集](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
 ![搭配回到頁首連結使用的箭頭圖示](../../analysis-services/instances/media/uparrow16x16.png "搭配回到頁首連結使用的箭頭圖示") [&#91;頁首&#93;](#Top)  
  
## 另請參閱  
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [資料庫快照集 &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  