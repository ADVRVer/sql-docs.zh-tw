---
title: "允許非管理員使用複寫監視器 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 27fb31025eee37e5de9d75b0433089fec8f8a3ea
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a>允許非管理員使用複寫監視器
  本主題描述如何允許非管理員藉由使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中使用複寫監視器。 「複寫監視器」可供身為下列角色成員的使用者使用：  
  
-   **系統管理員 (sysadmin)** 固定伺服器角色。  
  
     這些使用者可監視複寫，並且擁有變更複寫屬性的完全控制，例如，代理程式排程、代理程式設定檔等。  
  
-   散發資料庫中的 **replmonitor** 資料庫角色。  
  
     這些使用者可監視複寫，但無法變更任何複寫屬性。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [安全性](#Security)  
  
-   **若要允許非管理員使用複寫監視器，請使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 若要允許非管理員的人使用「複寫監視器」， **系統管理員 (sysadmin)** 固定伺服器角色的成員必須將使用者加入至散發資料庫，並將該使用者指派至 **replmonitor** 角色。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a>允許非管理員使用複寫監視器  
  
1.  在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中連接到散發者，然後展開伺服器節點。  
  
2.  展開 **[資料庫]**，展開 **[系統資料庫]**，並且展開散發資料庫 (預設名稱為 **distribution** )。  
  
3.  展開 **[安全性]**，以滑鼠右鍵按一下 **[使用者]**，再按一下 **[新增使用者]**。  
  
4.  輸入使用者名稱及使用者的登入。  
  
5.  選取 **[replmonitor]**的預設結構描述。  
  
6.  在 **[資料庫角色成員資格]** 方格中選取 **[replmonitor]** 。  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a>若要將使用者加入至 replmonitor 固定資料庫角色  
  
1.  在散發資料庫的「散發者」端，執行 [sp_helpuser &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)。 如果使用者未列於結果集中的 **UserName**，則必須使用 [CREATE USER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-user-transact-sql.md) 陳述式，授與使用者散發資料庫的存取權。  
  
2.  在散發資料庫的「散發者」端執行 [sp_helprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)，並指定 **replmonitor** 值給 **@rolename** 參數。 如果使用者列於結果集中的 **MemberName** ，則該使用者已屬於此角色。  
  
3.  如果使用者不屬於 **replmonitor** 角色，請在散發資料庫的「散發者」端執行 [sp_addrolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)。 針對 **replmonitor** @rolename **@rolename** 的值，並指定資料庫使用者的名稱或針對 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] @membername **@membername**中使用複寫監視器。  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a>若要從 replmonitor 固定資料庫角色移除使用者  
  
1.  若要確認使用者屬於 **replmonitor** 角色，請在散發資料庫的「散發者」端執行 [sp_helprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)，並指定 **replmonitor** 值給 **@rolename**。 如果使用者未列於結果集中的 **MemberName** ，則該使用者目前不屬於此角色。  
  
2.  如果使用者屬於 **replmonitor** 角色，請在散發資料庫的「散發者」端執行 [sp_droprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)。 針對 **replmonitor** @rolename **@rolename** 的值，並指定資料庫使用者的名稱或針對 **@membername**中使用複寫監視器。  
  
  
