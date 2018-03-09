---
title: "第 1 課：建立用於複寫的 Windows 帳戶 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
caps.latest.revision: "17"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 422f5bc66dc5b31889d4f790d61b5b95abf2fa7e
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>第 1 課：建立用於複寫的 Windows 帳戶
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 在這一課，您將建立 Windows 帳戶，以執行複寫代理程式。 您將在本機伺服器上，另外為下列代理程式建立 Windows 帳戶：  
  
|Agent|位置|帳戶名稱|  
|---------|------------|----------------|  
|快照集代理程式|發行者|\<*電腦名稱*>\repl_snapshot|  
|記錄讀取器代理程式|發行者|\<*電腦名稱*>\repl_logreader|  
|散發代理程式|發行者和訂閱者|\<*電腦名稱*>\repl_distribution|  
|合併代理程式|發行者和訂閱者|\<*電腦名稱*>\repl_merge|  
  
> [!NOTE]  
> 在複寫教學課程中，發行者和散發者會共用相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。 發行者和訂閱者可以共用相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體，但這不是必要條件。 如果發行者和訂閱者共用相同的執行個體，則不需要在訂閱者上建立帳戶的步驟。  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>在發行者端建立複寫代理程式的本機 Windows 帳戶  
  
1.  在發行者端，從 [控制台] 中的 [系統管理工具] 開啟 [電腦管理]。  
  
2.  在 [系統工具] 中，展開 [本機使用者和群組]。  
  
3.  以滑鼠右鍵按一下 [使用者]，然後按一下 [新增使用者]。  
  
4.  在 [使用者名稱] 方塊中輸入 **repl_snapshot**，並提供密碼和其他相關資訊，然後按一下 [建立]，以建立 repl_snapshot 帳戶。  
  
5.  重複執行先前的步驟，以建立 repl_logreader、repl_distribution 和 repl_merge 帳戶。  
  
6.  按一下 [ **關閉**]。  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>在訂閱者端建立複寫代理程式的本機 Windows 帳戶  
  
1.  在訂閱者端，從 [控制台] 中的 [系統管理工具] 開啟 [電腦管理]。  
  
2.  在 [系統工具] 中，展開 [本機使用者和群組]。  
  
3.  以滑鼠右鍵按一下 [使用者]，然後按一下 [新增使用者]。  
  
4.  在 [使用者名稱] 方塊中輸入 **repl_distribution**，並提供密碼和其他相關資訊，然後按一下 [建立]，以建立 repl_distribution 帳戶。  
  
5.  重複執行先前的步驟，以建立 repl_merge 帳戶。  
  
6.  按一下 [ **關閉**]。  
  
## <a name="next-steps"></a>Next Steps  
您已順利建立複寫代理程式的 Windows 帳戶。 下一步，您將設定快照集資料夾。 請參閱 [第 2 課：準備快照集資料夾](../../relational-databases/replication/lesson-2-preparing-the-snapshot-folder.md)。  
  
## <a name="see-also"></a>另請參閱  
[複寫代理程式概觀](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
  
