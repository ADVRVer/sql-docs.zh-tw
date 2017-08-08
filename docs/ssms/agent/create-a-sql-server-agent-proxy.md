---
title: "建立 SQL Server Agent Proxy | Microsoft Docs"
ms.custom: 
ms.date: 05/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: ceddddafe0c052d0477e218955949012818e9a73
ms.openlocfilehash: 2853583d3902f9b0da32e2b0e1c5a55b696d34e0
ms.contentlocale: zh-tw
ms.lasthandoff: 07/31/2017

---
# <a name="create-a-sql-server-agent-proxy"></a>建立 SQL Server Agent Proxy
此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql_md.md)]中建立 SQL Server Agent Proxy。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent Proxy 帳戶會定義作業步驟可以在其中執行的安全性內容。 每個 Proxy 都對應於一個安全性認證。 若要設定特定作業步驟的權限，請建立具有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 子系統之必要權限的 Proxy，然後將該 Proxy 指派給作業步驟。  
  
**本主題內容**  
  
-   **開始之前：**  
  
    [限制事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **若要使用下列項目建立 SQL Server Agent Proxy：**  
  
    [Transact-SQL](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>開始之前  
  
### <a name="Restrictions"></a>限制事項  
  
-   在建立 Proxy 之前，如果沒有認證可用，則必須先建立認證。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent Proxy 使用認證來儲存 Windows 使用者帳戶的相關資訊。 認證中所指定的使用者對執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 電腦必須具有「從網路存取這台電腦」的權限 (SeNetworkLogonRight)。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 會檢查 Proxy 的子系統存取權，而且每當作業步驟執行時，就會提供 Proxy 的存取權。 如果 Proxy 不再擁有子系統的存取權，作業步驟就會失效。 否則， [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 會模擬 Proxy 中所指定的使用者，並執行作業步驟。  
  
-   建立 Proxy 並不會改變 Proxy 認證中所指定之使用者的權限。 例如，您可能會為沒有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]執行個體之連接權限的使用者建立 Proxy， 在此情況下，使用該 Proxy 的作業步驟，便無法連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]。  
  
-   如果使用者的登入身分可以存取 Proxy，或者使用者隸屬於可存取 Proxy 的角色，該使用者就可以使用作業步驟中的 Proxy。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
  
-   只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員才擁有建立、修改或刪除 Proxy 帳戶的權限。 非 **系統管理員 (sysadmin)** 固定伺服器角色成員的使用者，必須加入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] msdb **資料庫中的下列其中一個** Agent 固定資料庫角色，才可使用 Proxy： **SQLAgentUserRole**、 **SQLAgentReaderRole**或 **SQLAgentOperatorRole**。  
  
-   如果除了 Proxy 之外還要建立認證，需要 **ALTER ANY CREDENTIAL** 權限。  
  
## <a name="SSMSProcedure"></a>使用 SQL Server Management Studio  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>若要建立 SQL Server Agent Proxy  
  
1.  在 **[物件總管]**中，按一下加號展開要建立 SQL Server Agent Proxy 的伺服器。  
  
2.  按一下加號展開 **[SQL Server Agent]**。  
  
3.  以滑鼠右鍵按一下 [Proxy] 資料夾，然後選取 [新增 Proxy]。  
  
4.  在 **[新 Proxy 帳戶]** 對話方塊，於 **[一般]** 頁面上的 **[Proxy 名稱]** 方塊中輸入 Proxy 帳戶的名稱。  
  
5.  在 **[認證名稱]** 方塊中，輸入 Proxy 帳戶將使用之安全性認證的名稱。  
  
6.  在 **[說明]** 方塊中，輸入 Proxy 帳戶的說明。  
  
7.  在 **[對下列子系統有效]**下，選取此 Proxy 的適當子系統。  
  
8.  在 **[主體]** 頁面上，加入或移除登入或角色，藉此授與或移除 Proxy 帳戶的存取。  
  
9. 完成後，請按一下 **[確定]**。  
  
## <a name="TsqlProcedure"></a>使用 Transact-SQL  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>若要建立 SQL Server Agent Proxy  
  
1.  在 **[物件總管]**中，連接到 [!INCLUDE[ssDE](../../includes/ssde_md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns
    -- the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to 
    -- the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
如需詳細資訊，請參閱：  
  
-   [CREATE CREDENTIAL (Transact-SQL)](http://msdn.microsoft.com/en-us/d5e9ae69-41d9-4e46-b13d-404b88a32d9d)  
  
-   [sp_add_proxy (Transact-SQL)](http://msdn.microsoft.com/en-us/cb59df37-f103-439b-bec1-2871fb669a8b)  
  
-   [sp_grant_proxy_to_subsystem (Transact-SQL)](http://msdn.microsoft.com/en-us/866aaa27-a1e0-453a-9b1b-af39431ad9c2)  
  

