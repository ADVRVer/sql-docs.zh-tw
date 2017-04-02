---
title: "使用參數化篩選管理合併式發行集的資料分割 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "partitions [SQL Server replication]"
  - "merge replication partitions [SQL Server replication], SQL Server Management Studio"
  - "參數化篩選 [SQL Server 複寫], 資料分割管理"
ms.assetid: fb5566fe-58c5-48f7-8464-814ea78e6221
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# 使用參數化篩選管理合併式發行集的資料分割
  本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中使用參數化篩選管理合併式發行集的資料分割。 參數化資料列篩選器可用來產生非重疊的資料分割。 這些資料分割可以限制為只有一個訂閱能收到給定資料分割。 在這種狀況中，大量的訂閱者會導致大量的資料分割，而這種情況則需要同等數量的資料分割快照集。 如需詳細資訊，請參閱 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [建議](#Recommendations)  
  
-   **若要使用參數化篩選管理合併式發行集的資料分割，請使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Recommendations"></a> 建議  
  
-   如果您為複寫拓撲編寫指令碼 (建議您如此做)，則發行集指令碼將包含呼叫建立資料分割的預存程序。 指令碼提供所建立資料分割的參考，並提供必要時重新建立一或多個資料分割的方式。 如需詳細資訊，請參閱 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)。  
  
-   當發行集擁有會產生具有非重疊資料分割之訂閱的參數化篩選時，以及遺失了特定訂閱而需要重新建立時，您必須執行下列作業：移除先前訂閱的資料分割、重新建立訂閱，然後重新建立資料分割。 如需詳細資訊，請參閱 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)。 複寫會在發行集建立指令碼產生時，針對現有的「訂閱者」資料分割產生建立指令碼。 如需詳細資訊，請參閱 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 管理資料分割上 **資料分割** 頁面 **發行集屬性-\< 發行集>** 對話方塊。 如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)＞。 您可以在此頁面中：建立和刪除資料分割；允許「訂閱者」初始化快照集產生和傳遞；為一個或多個資料分割產生快照集；清除快照集。  
  
#### 若要建立資料分割  
  
1.  在 **資料分割** 頁面 **發行集屬性-\< 發行集>** 對話方塊中，按一下 [ **新增**。  
  
2.  在 **加入資料分割** ] 對話方塊中，輸入的值 **host_name （)** 及/或 **suser_sname （)** 與您想要建立資料分割相關聯的值。  
  
3.  選擇性地指定重新整理快照集的排程：  
  
    1.  選取 **排程在下列時間執行的這個資料分割快照集代理程式**  
  
    2.  接受重新重理快照集的預設排程，或按一下 **[變更]** 以指定其他排程。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### 若要刪除資料分割  
  
1.  在 **[資料分割]** 頁面上，從方格中選取一個資料分割。  
  
2.  按一下 **[刪除]**。  
  
#### 若要允許訂閱者初始化快照集的產生與傳遞  
  
1.  在 **[資料分割]** 頁面上，選取 **[新的訂閱者嘗試進行同步處理時，自動定義資料分割並依需要產生快照]**。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### 若要產生資料分割的快照集  
  
1.  在 **[資料分割]** 頁面上，從方格中選取一個資料分割。  
  
2.  按一下 **[立即產生選取的快照集]**。  
  
#### 若要清除資料分割的快照集  
  
1.  在 **[資料分割]** 頁面上，從方格中選取一個資料分割。  
  
2.  按一下 **[清除現有快照集]**。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 若要使用參數化篩選以更好的方式管理發行集，可以使用複寫預存程序，以程式設計的方式列舉現有的資料分割。 您也可以建立及刪除現有的資料分割。 您可取得下列有關現有資料分割的資訊：  
  
-   資料分割的篩選方式 (使用 [SUSER_SNAME & #40。TRANSACT-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md) 或 [HOST_NAME & #40。Transact-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md))。  
  
-   產生資料分割快照集的工作名稱。  
  
-   上次執行資料分割快照集作業的時間。  
  
 雖然兩部分快照集的第二部份可以在初始化新訂閱時視需要而產生，但下列程序可用來控制產生此快照集的方式，並在最方便的時候預先產生此快照集。 如需相關資訊，請參閱 [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)。  
  
#### 若要在現有的資料分割上檢視資訊  
  
1.  在發行集資料庫的發行者，執行 [sp_helpmergepartition & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md)。 指定 **@publication**出版物的名稱。 （選擇性）指定 **@suser_sname** 或 **@host_name** 傳回單一的篩選準則為基礎的資訊。  
  
#### 若要定義新的資料分割並產生新的資料分割快照集  
  
1.  在發行集資料庫的發行者，執行 [sp_addmergepartition & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)。 指定 **@publication**的發行集名稱，並針對下列其中一個項目定義資料分割的參數化值：  
  
    -   **@suser_sname** -時所傳回的值定義參數化的篩選 [SUSER_SNAME & #40。TRANSACT-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md)。  
  
    -   **@host_name** -時所傳回的值定義參數化的篩選 [HOST_NAME & #40。TRANSACT-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md)。  
  
2.  建立並初始化這個新資料分割的參數化快照集。 如需詳細資訊，請參閱 [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。  
  
#### 若要刪除資料分割  
  
1.  在發行集資料庫的發行者，執行 [sp_dropmergepartition & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)。 指定 **@publication** 的發行集名稱，並針對下列其中一個項目定義資料分割的參數化值：  
  
    -   **@suser_sname** -時所傳回的值定義參數化的篩選 [SUSER_SNAME & #40。TRANSACT-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md)。  
  
    -   **@host_name** -時所傳回的值定義參數化的篩選 [HOST_NAME & #40。TRANSACT-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md)。  
  
     這也會移除資料分割的快照集作業和快照集檔案。  
  
##  <a name="RMOProcedure"></a> 使用 Replication Management Objects (RMO)  
 若要使用參數化篩選以更好的方式管理發行集，可以使用 Replication Management Objects (RMO)，以程式設計的方式建立新的「訂閱者」資料分割、列舉現有的「訂閱者」資料分割，以及刪除「訂閱者」資料分割。 如需有關如何建立「訂閱者」資料分割的詳細資訊，請參閱＜ [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)＞。 您可取得下列有關現有資料分割的資訊：  
  
-   資料分割所根據的值和篩選函數。  
  
-   為「訂閱者」產生參數化快照集的作業名稱。  
  
-   上次執行參數化快照集作業的時間。  
  
#### 若要在現有的資料分割上檢視資訊  
  
1.  建立連接到 「 發行者 」 使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別。  
  
2.  建立的執行個體 <xref:Microsoft.SqlServer.Replication.MergePublication> 類別。 設定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 發行集，並設定屬性 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 步驟 1 中建立。  
  
3.  呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法來取得物件的屬性。 如果此方法傳回 **false**，則表示步驟 2 中的發行集屬性定義不正確，或者該發行集不存在。  
  
4.  呼叫 <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> 方法，並將結果傳遞給陣列 <xref:Microsoft.SqlServer.Replication.MergePartition> 物件。  
  
5.  每個 <xref:Microsoft.SqlServer.Replication.MergePartition> 物件陣列中，取得想要的任何屬性。  
  
#### 若要刪除現有的資料分割  
  
1.  建立連接到 「 發行者 」 使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別。  
  
2.  建立的執行個體 <xref:Microsoft.SqlServer.Replication.MergePublication> 類別。 設定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 發行集，並設定屬性 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 步驟 1 中建立。  
  
3.  呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法來取得物件的屬性。 如果此方法傳回 **false**，則表示步驟 2 中的發行集屬性定義不正確，或者該發行集不存在。  
  
4.  呼叫 <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> 方法，並將結果傳遞給陣列 <xref:Microsoft.SqlServer.Replication.MergePartition> 物件。  
  
5.  每個 <xref:Microsoft.SqlServer.Replication.MergePartition> 物件陣列中，判斷是否應刪除的磁碟分割。 此決策通常是依據的值 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> 屬性或 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> 屬性。  
  
6.  呼叫 <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> 方法 <xref:Microsoft.SqlServer.Replication.MergePublication> 步驟 2 中的物件。 傳遞 <xref:Microsoft.SqlServer.Replication.MergePartition> 步驟 5 中的物件。  
  
7.  針對每個刪除的資料分割重複步驟 6。  
  
## 另請參閱  
 [參數化資料列篩選器](../../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [含參數化篩選之合併式發行集的快照集](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  