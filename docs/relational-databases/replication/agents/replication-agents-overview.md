---
title: "複寫代理程式概觀 | Microsoft Docs"
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
  - "散發代理程式"
  - "代理程式 [SQL Server 複寫]"
  - "佇列讀取器代理程式, 關於佇列讀取器代理程式"
  - "佇列讀取器代理程式"
  - "合併代理程式, 關於合併代理程式"
  - "記錄讀取器代理程式, 關於記錄讀取器代理程式"
  - "複寫 [SQL Server], 代理程式和設定檔"
  - "記錄讀取器代理程式"
  - "散發代理程式, 關於散發代理程式"
  - "代理程式 [SQL Server 複寫], 關於代理程式"
  - "合併代理程式"
  - "快照集代理程式, 關於快照集代理程式"
  - "快照集代理程式"
ms.assetid: a35ecd7d-f130-483c-87e3-ddc8927bb91b
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# 複寫代理程式概觀
  複寫使用了許多名為代理程式的獨立程式，以執行與追蹤變更和散發資料有關的工作。 依預設，複寫代理程式作為在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 中排定的作業來執行，且必須執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 方可執行這些作業。 複寫代理程式也可以從命令列執行，或透過使用 Replication Management Objects (RMO) 的應用程式執行。 複寫代理程式可以透過「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫監視器」和 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 進行管理。  
  
## SQL Server Agent  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理程式主控和排程複寫中使用的代理程式，並提供簡單的方法來執行複寫代理程式。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理程式也會控制和監視複寫以外的作業。 如需詳細資訊，請參閱 [Configure SQL Server Agent](../../../ssms/agent/configure-sql-server-agent.md)。  
  
> [!IMPORTANT]  
>  依預設，安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時會停用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 服務，除非明確選擇在安裝期間自動啟動該服務。 如需有關啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理程式服務，請參閱 [啟動、 停止或暫停 SQL Server Agent 服務](../../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)。  
  
## 快照集代理程式  
 「快照集代理程式」通常搭配各種類型的複寫使用， 它會準備已發行資料表和其他物件的結構描述和初始資料檔、儲存快照集檔案，並記錄散發資料庫中同步處理的相關資訊。 快照集代理程式於發行者端執行。 如需詳細資訊，請參閱 [複寫快照集代理程式](../../../relational-databases/replication/agents/replication-snapshot-agent.md)。  
  
## 記錄讀取器代理程式  
 「記錄讀取器代理程式」(Log Reader Agent) 可搭配異動複寫來使用。 它可將標示為複寫的交易，自「發行者」的交易記錄移至散發資料庫中。 每個使用異動複寫發行的資料庫都擁有其自己的「記錄讀取器代理程式」，該代理程式在「散發者」端執行並連接到「發行者」(「散發者」可與「發行者」在同一台電腦)。 如需詳細資訊，請參閱 [Replication Log Reader Agent](../../../relational-databases/replication/agents/replication-log-reader-agent.md)。  
  
## 散發代理程式  
 「散發代理程式」(Distribution Agent) 可搭配快照式複寫和異動複寫來使用。 它可將初始快照集套用至「訂閱者」，並將散發資料庫中的交易移至「訂閱者」。 「散發代理程式」在發送訂閱的「散發者」端或是提取訂閱的「訂閱者」端執行。 如需詳細資訊，請參閱 [複寫散發代理程式](../../../relational-databases/replication/agents/replication-distribution-agent.md)。  
  
## [合併代理程式]  
 「合併代理程式」(Merge Agent) 可搭配合併式複寫使用。 它可將初始快照集套用到「訂閱者」，移動並使累加的資料變更一致。 每個合併訂閱都有其「合併代理程式」，以連接「發行者」和「訂閱者」，並更新這兩者。 「合併代理程式」在發送訂閱的「散發者」端或是提取訂閱的「訂閱者」端執行。 依預設，「合併代理程式」將變更從「訂閱者」上傳到「發行者」，然後再將變更從「發行者」下載至「訂閱者」。 如需詳細資訊，請參閱 [Replication Merge Agent](../../../relational-databases/replication/agents/replication-merge-agent.md)。  
  
## 佇列讀取器代理程式  
 「佇列讀取器代理程式」與具有佇列更新選項的異動複寫搭配使用。 代理程式在「散發者」端執行，並且將在「訂閱者」端所作的變更移回至「發行者」。 它不像「散發代理程式」和「合併代理程式」，只存在一個「佇列讀取器代理程式」的執行個體，來服務所有的「發行者」和指定散發資料庫的發行集。 如需 「 佇列讀取器代理程式的詳細資訊，請參閱 [複寫佇列讀取器代理程式](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)。 如需有關可更新訂閱的詳細資訊，請參閱 [交易式複寫的可更新訂閱](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)。  
  
## 複寫維護作業  
 複寫擁有許多依排程和視需要執行維護的維護作業。 如需詳細資訊，請參閱 [複寫代理程式管理](../../../relational-databases/replication/agents/replication-agent-administration.md)。  
  
## 另請參閱  
 [啟動和停止複寫代理程式 & #40。SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [執行複寫維護作業 & #40。SQL Server Management Studio & #41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)   
 [複寫代理程式可執行檔概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [複寫代理程式管理](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  