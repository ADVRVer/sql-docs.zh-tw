---
title: "同步處理發送訂閱 | Microsoft Docs"
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
  - "同步處理 [SQL Server 複寫], 發送訂閱"
  - "訂閱 [SQL Server 複寫], 發送"
  - "發送訂閱 [SQL Server 複寫], 同步處理"
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# 同步處理發送訂閱
  本主題描述如何同步處理中的發送訂閱 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ，[複寫代理程式](../../relational-databases/replication/agents/replication-agents-overview.md), ，或 Replication Management Objects (RMO)。  
  
 **本主題內容**  
  
-   **若要同步處理發送訂閱，請使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [複寫代理程式](#ReplProg)  
  
     [Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 訂閱是由散發代理程式 (適用於快照式與異動複寫) 或合併代理程式 (適用於合併式複寫) 同步處理。 代理程式可以繼續執行、視需要執行，或是依照排程執行。 如需指定同步處理排程的詳細資訊，請參閱 [指定同步處理排程](../../relational-databases/replication/specify-synchronization-schedules.md)。  
  
 需要時從  中的 **[本機發行集]** 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 the **[所有訂閱]** 索引標籤同步處理訂閱。 Oracle 發行集的訂閱無法在需要時從「訂閱者」同步處理。 如需啟動複寫監視器的詳細資訊，請參閱 [啟動複寫監視器](../../relational-databases/replication/monitor/start-the-replication-monitor.md)。  
  
#### 需要時在 Management Studio 上同步處理發送訂閱 (發行者端)  
  
1.  連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。  
  
2.  展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。  
  
3.  展開您要同步處理其訂閱的發行集。  
  
4.  以滑鼠右鍵按一下您想要同步處理，然後按一下 [的訂閱 **檢視同步處理狀態**。  
  
5.  在 **檢視同步處理狀態-\< 訂閱者>: \< u>** 對話方塊中，按一下 [ **啟動**。 同步處理完成後，會顯示 **[同步處理已完成]** 的訊息。  
  
6.  按一下 [ **關閉**]。  
  
#### 需要時在 Management Studio 上同步處理發送訂閱 (訂閱者端)  
  
1.  連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的訂閱者，然後展開伺服器節點。  
  
2.  展開 **[複寫]** 資料夾，然後展開 **[本機訂閱]** 資料夾。  
  
3.  以滑鼠右鍵按一下您想要同步處理，然後按一下 [的訂閱 **檢視同步處理狀態**。  
  
4.  接著會顯示有關建立連接到「散發者」的訊息。 按一下 **[確定]**。  
  
5.  在 **檢視同步處理狀態-\< 訂閱者>: \< u>** 對話方塊中，按一下 [ **啟動**。 同步處理完成後，會顯示 **[同步處理已完成]** 的訊息。  
  
6.  按一下 [ **關閉**]。  
  
#### 需要時在複寫監視器中同步處理發送訂閱  
  
1.  在複寫監視器中，展開左窗格裡的發行者群組，展開發行者，然後按一下發行集。  
  
2.  按一下 **[所有訂閱]** 索引標籤。  
  
3.  以滑鼠右鍵按一下您想要同步處理，然後按一下 [的訂閱 **啟動同步處理**。  
  
4.  若要檢視同步處理的進度，以滑鼠右鍵按一下訂閱，然後按一下 **檢視詳細資料**。  
  
##  <a name="ReplProg"></a> 使用複寫代理程式  
 發送訂閱可透過程式設計方式加以同步處理，以及視需要從命令提示字元叫用適當的複寫代理程式可執行檔加以同步處理。 叫用的複寫代理程式可執行檔取決於發送訂閱所屬的發行集類型。  
  
#### 啟動散發代理程式，以同步處理交易式發行集的發送訂閱  
  
1.  從命令提示字元或是散發者上的批次檔中，執行 **distrib.exe**。 指定下列命令列引數：  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Distributor**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType = 0**  
  
     無果您正在使用「SQL Server 驗證」，您也必須指定下列引數：  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode = 0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode = 0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode = 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
#### 啟動合併代理程式，以同步處理合併式發行集的發送訂閱  
  
1.  從命令提示字元或是散發者上的批次檔中，執行 **replmerg.exe**。 指定下列命令列引數：  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Publication**  
  
    -   **-Distributor**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType = 0**  
  
     無果您正在使用「SQL Server 驗證」，您也必須指定下列引數：  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode = 0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode = 0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode = 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
###  <a name="TsqlExample"></a> 範例 (複寫代理程式)  
 下列範例會啟動散發代理程式，以同步處理發送訂閱。  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksProductsTran  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4  
  
```  
  
 下列範例會啟動合併代理程式，以同步處理發送訂閱。  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksSalesOrdersMerge  
  
REM -- Start the Merge Agent.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher %Publisher%   
-Subscriber  %Subscriber%  -Distributor %Publisher% -PublisherDB  %PublicationDB%   
-SubscriberDB %SubscriptionDB% -Publication %Publication% -PublisherSecurityMode 1   
-OutputVerboseLevel 3  -Output -SubscriberSecurityMode 1  -SubscriptionType 0   
-DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> 使用 Replication Management Objects (RMO)  
 您可以使用 Replication Management Objects (RMO) 和對複寫代理程式功能的 Managed 程式碼存取，以程式設計的方式同步處理發送訂閱。 用於同步處理發送訂閱的類別依該訂閱所屬的發行集類型而定。  
  
> [!NOTE]  
>  如果您要啟動自發執行的同步處理而不影響應用程式，請非同步啟動代理程式。 不過，如果要監視同步處理的結果並在同步處理期間從代理程式接收回撥 (例如，如果要顯示進度列)，您就應該同步啟動代理程式。 您必須為「 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 訂閱者」同步啟動代理程式。  
  
#### 若要同步處理快照式或交易式發行集的發送訂閱  
  
1.  建立連接到散發者 」 使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別。  
  
2.  建立的執行個體 <xref:Microsoft.SqlServer.Replication.TransSubscription> 類別，並設定下列屬性︰  
  
    -   發行集資料庫名稱 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>。  
  
    -   訂閱所屬的發行集名稱 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>。  
  
    -   訂閱資料庫的名稱 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>。  
  
    -   訂閱者的名稱 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>。  
  
    -   步驟 1 中建立的連線 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>。  
  
3.  呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法來取得剩餘的訂閱屬性。 如果此方法傳回 **false**，請確認該訂閱存在。  
  
4.  以下列其中一種方式啟動「散發者」上的「散發代理程式」：  
  
    -   呼叫 <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> 方法的執行個體上 <xref:Microsoft.SqlServer.Replication.TransSubscription> 從步驟 2。 此方法會以非同步方式啟動散發代理程式，並且控制項會在代理程式作業執行時立即傳回至應用程式。 如果值是建立訂閱時，無法呼叫這個方法 **false** 的 <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>。  
  
    -   取得執行個體 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> 類別是從 <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> 屬性，並呼叫 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> 方法。 此方法會同步啟動代理程式，而控制項仍會停留於正在執行的代理程式作業。 您可以在同步執行期間處理 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> 代理程式正在執行的事件。  
  
#### 若要同步處理合併式發行集的發送訂閱  
  
1.  建立連接到散發者 」 使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別。  
  
2.  建立的執行個體 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 類別，並設定下列屬性︰  
  
    -   發行集資料庫名稱 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>。  
  
    -   訂閱所屬的發行集名稱 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>。  
  
    -   訂閱資料庫的名稱 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>。  
  
    -   訂閱者的名稱 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>。  
  
    -   步驟 1 中建立的連線 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>。  
  
3.  呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法來取得剩餘的訂閱屬性。 如果此方法傳回 **false**，請確認該訂閱存在。  
  
4.  以下列其中一種方式啟動「散發者」上的「合併代理程式」：  
  
    -   呼叫 <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> 方法的執行個體上 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 從步驟 2。 此方法會以非同步方式啟動合併代理程式，並且控制項會在代理程式作業執行時立即傳回至應用程式。 如果值是建立訂閱時，無法呼叫這個方法 **false** 的 <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>。  
  
    -   取得執行個體 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> 類別是從 <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> 屬性，並呼叫 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> 方法。 此方法會同步啟動「合併代理程式」，而控制項仍會停留於正在執行的代理程式作業。 在同步執行，您可以處理 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> 代理程式正在執行的事件。  
  
###  <a name="PShellExample"></a> 範例 (RMO)  
 此範例同步處理交易式發行集的發送訂閱，其中代理程式會使用代理程式作業非同步啟動。  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub_withjob)]  
  
 此範例同步處理交易式發行集的發送訂閱，其中代理程式會同步啟動。  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub)]  
  
 此範例同步處理合併式發行集的發送訂閱，其中代理程式會使用代理程式作業非同步啟動。  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub_withjob)]  
  
 此範例同步處理合併式發行集的發送訂閱，其中代理程式會同步啟動。  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub)]  
  
## 另請參閱  
 [Replication Management Objects 概念。](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [同步處理資料](../../relational-databases/replication/synchronize-data.md)   
 [複寫安全性最佳做法](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  