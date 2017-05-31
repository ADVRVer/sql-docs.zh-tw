---
title: "設定 SQL Server Agent | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e433dd732e153213da84aa9a1444f9255cc5a4d5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/11/2017

---
# <a name="configure-sql-server-agent"></a>設定 SQL Server Agent
本主題描述如何在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 期間指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Agent 的一些組態選項。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]管理物件 (SMO) 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 預存程序內才有完整的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 組態選項集合可用。  
  
**本主題內容**  
  
-   **開始之前：**  
  
    [限制事項](#Restrictions)  
  
    [Security](#Security)  
  
-   [若要設定 SQL Server Agent](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>開始之前  
  
### <a name="Restrictions"></a>限制事項  
  
-   在 **的 [物件總管] 中，按一下** [SQL Server Agent] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ，以管理作業、運算子、警示與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 服務。 不過，只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。  
  
-   容錯移轉叢集執行個體上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 服務或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 服務不應該啟用自動重新啟動。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)](系統管理員) 固定伺服器角色的成員。 此帳戶必須擁有下列 Windows 權限：  
  
-   以服務登入 (SeServiceLogonRight)  
  
-   取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)  
  
-   略過跨越檢查 (SeChangeNotifyPrivilege)  
  
-   調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)  
  
如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 服務帳戶所需之 Windows 權限的詳細資訊，請參閱＜ [選取 SQL Server Agent 服務的帳戶](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) ＞及＜ [設定 Windows 服務帳戶](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)＞。  
  
## <a name="SSMSProcedure"></a>使用 SQL Server Management Studio  
  
#### <a name="to-configure-sql-server-agent"></a>若要設定 SQL Server Agent  
  
1.  按一下 **[開始]** 按鈕，然後按一下 **[開始]**  功能表上的 **[控制台]**。  
  
2.  在 [控制台] 中，依序按一下 **[系統及安全性]**和 **[系統管理工具]**，然後選取 **[本機安全性原則]**。  
  
3.  在 [本機安全性原則] 中，按一下＞形箭號展開 **[本機原則]** 資料夾，然後按一下 **[使用者權限指派]** 資料夾。  
  
4.  以滑鼠右鍵按一下您要設定搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 使用的權限，然後選取 [屬性]。  
  
5.  在權限的屬性對話方塊中，確認已列出用於執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 的帳戶。 如果未列出，請按一下 **[加入使用者或群組]**，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] [選取使用者、電腦、服務帳戶或群組] **對話方塊中輸入執行** Agent 的帳戶，然後按一下 **[確定]**。  
  
6.  針對您要加入以搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 執行的每項權限重複這項操作。 完成後，請按一下 **[確定]**。  
  

