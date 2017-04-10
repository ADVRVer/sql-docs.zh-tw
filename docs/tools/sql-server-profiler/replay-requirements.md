---
title: "重新執行需求 | Microsoft Docs"
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
  - "事件類別 [SQL Server], 重新執行追蹤"
  - "追蹤 [SQL Server], 重新執行"
  - "重新執行追蹤"
  - "TSQL_Replay 範本 [SQL Server]"
ms.assetid: 0e01dfc7-84b9-47f6-8bf7-b0656df4fa7d
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# 重新執行需求
  若要使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或分散式重新執行公用程式來重新執行追蹤資料，您必須在追蹤中擷取特定的事件類別和資料行集合。 如果 **TSQL_Replay** 追蹤範本用來設定之後用於重新執行的追蹤，預設將啟用這些設定。 本主題會說明這些設定和其他重新執行需求。  
  
> [!NOTE]  
>  我們建議您使用分散式重新執行公用程式來重新執行密集的 OLTP 應用程式 (具有許多使用中並行連接或高輸送量)。 分散式重新執行公用程式可以從多部電腦重新執行追蹤資料，並有效模擬關鍵任務的工作負載。 如需詳細資訊，請參閱 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)。  
  
## 重新執行所需的事件類別  
 若要由 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 重新執行，除了您要監視的其他任何事件類別以外，還必須在追蹤中擷取下列事件類別集合：  
  
-   **CursorClose** (只有重新執行伺服端資料指標時才需要)  
  
-   **CursorExecute** (只有重新執行伺服端資料指標時才需要)  
  
-   **CursorOpen** (只有重新執行伺服端資料指標時才需要)  
  
-   **CursorPrepare** (只有重新執行伺服端資料指標時才需要)  
  
-   **CursorUnprepare** (只有重新執行伺服端資料指標時才需要)  
  
-   **稽核登入**  
  
-   **稽核登出**  
  
-   **ExistingConnection**  
  
-   **RPC Output Parameter**  
  
-   **RPC:Completed**  
  
-   **RPC:Starting**  
  
-   **Exec Prepared SQL** (只有重新執行伺服器端備妥的 SQL 陳述式時才需要)  
  
-   **Prepare SQL** (只有重新執行伺服端備妥的 SQL 陳述式時才需要)  
  
-   **SQL:BatchCompleted**  
  
-   **SQL:BatchStarting**  
  
## 重新執行所需的資料行  
 若要能夠重新執行追蹤，除了要擷取的其他任何資料行之外，還必須在追蹤中擷取以下資料行：  
  
-   **Event Class**  
  
-   **EventSequence**  
  
-   **TextData**  
  
-   **Application Name**  
  
-   **LoginName**  
  
-   **DatabaseName**  
  
-   **資料庫識別碼**  
  
-   **ClientProcessID**  
  
-   **HostName**  
  
-   **ServerName**  
  
-   **Binary Data**  
  
-   **SPID**  
  
-   **Start Time**  
  
-   **EndTime**  
  
-   **IsSystem**  
  
-   **NTDomainName**  
  
-   **NTUserName**  
  
-   **錯誤**  
  
> [!NOTE]  
>  對追蹤使用追蹤範本 **TSQL_Replay**，擷取重新執行的資料。  
  
## 其他重新執行需求  
 在 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，重新執行會檢查出現的必要事件和資料行。 這個變更可協助改善重新執行的精確度，而且當有必要資料遺失時，進行重新執行的疑難排解就不需要猜測。 當追蹤內遺失必要的資料時，重新執行會傳回一則錯誤，並停止重新執行該檔案。  
  
 若要在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的伺服器 (目標)，而非原始追蹤的伺服器 (來源) 重新執行追蹤，請確定已完成下列各項：  
  
-   追蹤中包含的所有登入與使用者必須已在目標上建立，而且要與來源一樣在相同的資料庫中。  
  
-   目標中的所有登入與使用者，其權限必須與在來源中具有的權限相同。  
  
-   所有登入密碼必須與執行重新執行的使用者之密碼一樣。  
  
-   目標上的資料庫識別碼必須與來源上的一樣。 不過，如果不相同，若追蹤內有 **DatabaseName** 的話， 就可以據以執行比對作業。  
  
-   追蹤中包含之每個登入的預設資料庫必須設成 (在目標上) 登入的個別目標資料庫。 例如，要重新執行的追蹤包含 **Fred** 登入的活動，其位於來源的資料庫 **Fred_Db** 中。 因此在目標上，**Fred** 登入的預設資料庫必須設成符合 **Fred_Db** 的資料庫 (即使資料庫名稱不同亦然)。 若要設定登入的預設資料庫，可使用 **sp_defaultdb** 系統預存程序。  
  
 重新執行與找不到或不正確之登入相關的事件，會造成重新執行錯誤，但重新執行作業仍會繼續。  
  
 如需有關重做追蹤時所需之權限的詳細資訊，請參閱＜ [Permissions Required to Run SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)＞。  
  
## 另請參閱  
 [重新執行追蹤資料表 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [重新執行追蹤檔案 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [SQL Server 事件類別參考](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_defaultdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md)   
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  