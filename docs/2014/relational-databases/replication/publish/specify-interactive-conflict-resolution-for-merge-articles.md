---
title: 指定合併發行項的互動式衝突解決方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], interactive resolvers
- interactive conflict resolution [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: e298dea0-b5ef-4907-a745-cfad9793653f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 710db513395aa5a9c51df55b54bafbdc425ecb5d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52749291"
---
# <a name="specify-interactive-conflict-resolution-for-merge-articles"></a>指定合併發行項的互動式衝突解決方法
  本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中針對合併發行項指定互動式衝突解決方法。  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫提供互動式解決器，可讓您在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager 中於需要同步處理期間手動解決衝突。 在啟用互動式解決方案之後，在同步處理期間會使用「互動解決器」以互動方式解決衝突。 互動解決器可以從 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager 使用。 如需詳細資訊，請參閱[使用 Windows Synchronization Manager 同步處理訂閱 &#40;Windows Synchronization Manager&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md)。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [建議](#Recommendations)  
  
-   **若要指定合併發行項的互動式衝突解決方法，請使用：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Recommendations"></a> 建議  
  
-   如果是在 Windows Synchronization Manager 之外執行同步處理 (如 SQL Server Management Studio 或複寫監視器中已排程的同步處理或視需要同步處理)，則不需要使用者的介入，就會使用針對發行項指定的預設衝突解決方式來自動解決衝突。 如需詳細資訊，請參閱 [Interactive Conflict Resolution](../merge/advanced-merge-replication-conflict-interactive-resolution.md)。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-enable-interactive-conflict-resolution-for-an-article"></a>若要啟用發行項的互動式衝突解決方案  
  
1.  在 [新增發行集精靈] 的 [發行項] 頁面上，或是在 [發行集屬性 - \<發行集>] 對話方塊中，選取一個資料表。 如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。  
  
2.  按一下 **[發行項屬性]**，然後按一下 **[設定反白顯示資料表發行項的屬性]** 或 **[設定所有資料表發行項的屬性]**。  
  
3.  在 [發行項屬性 - \<發行項>] 或 [發行項屬性 - \<發行項類型>] 頁面上，按一下 [解析程式] 索引標籤。  
  
4.  選取 **[允許訂閱者在依要求同步期間，以互動方式解決衝突]**。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  如果您在 [發行集屬性 - \<發行集>] 對話方塊中，請按一下 [確定] 儲存並關閉對話方塊。  
  
#### <a name="to-specify-that-a-subscription-should-use-interactive-conflict-resolution"></a>若要指定訂閱應使用互動式衝突解決方案  
  
1.  在 **訂用帳戶屬性-\<訂閱者 >:\<訂閱資料庫 >** 對話方塊方塊中，指定的值 **，則為 True**如**互動方式解決衝突**選項。 如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Push Subscription Properties](../view-and-modify-push-subscription-properties.md) ＞與＜ [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md)＞。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 您可以透過程式設計方式指定在建立合併式發行集的提取訂閱時，訂閱者將使用此圖形化介面來解決發行項衝突。 只有支援此選項之發行項中的衝突才會顯示在互動式解決器中。  
  
#### <a name="to-create-a-merge-pull-subscription-that-uses-the-interactive-resolver"></a>建立使用互動式解決器的合併式提取訂閱  
  
1.  在發行集資料庫的發行者上執行 [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，指定 **@publication**中針對合併發行項指定互動式衝突解決方法。 請記下結果集中每一個發行項的 **allow_interactive_resolver** 值 (互動式解決器將針對它來使用)。  
  
    -   如果這個值是 **1**，將會使用互動式解決器。  
  
    -   如果這個值是 **0**，您必須先針對每一個發行項啟用互動式解決器。 若要這樣做，請執行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)，指定 **@publication**、 **@article**，並針對 **allow_interactive_resolver** 指定 **@property**的值及針對 **true** 指定 **@value**中針對合併發行項指定互動式衝突解決方法。  
  
2.  在訂閱資料庫的訂閱者上，執行 [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)。 如需詳細資訊，請參閱 [建立提取訂閱](../create-a-pull-subscription.md)。  
  
3.  在訂閱資料庫的訂閱者上，執行 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)並指定下列參數：  
  
    -   **@publisher**、 **@publisher_db** (發行的資料庫) 和 **@publication**中針對合併發行項指定互動式衝突解決方法。  
  
    -   為 **true** 指定 **@enabled_for_syncmgr**中針對合併發行項指定互動式衝突解決方法。  
  
    -   為 **true** 指定 **@use_interactive_resolver**中針對合併發行項指定互動式衝突解決方法。  
  
    -   合併代理程式所需的安全性帳戶資訊。 如需詳細資訊，請參閱 [Create a Pull Subscription](../create-a-pull-subscription.md)。  
  
4.  在發行集資料庫的發行者上，執行 [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql)。  
  
#### <a name="to-define-an-article-that-supports-the-interactive-resolver"></a>定義支援互動式解決器的發行項  
  
1.  在發行集資料庫的發行者上，執行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。 針對 **@publication**指定發行項所屬的發行集名稱、針對 **@article**指定發行項名稱、針對 **@source_object**的值及針對 **true** 指定 **@allow_interactive_resolver**中針對合併發行項指定互動式衝突解決方法。 如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。  
  
## <a name="see-also"></a>另請參閱  
 [檢視並解決合併式發行集的資料衝突 &#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)   
 [Interactive Conflict Resolution](../merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
  
