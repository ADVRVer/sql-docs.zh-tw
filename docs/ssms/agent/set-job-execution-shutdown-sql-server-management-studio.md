---
title: "設定作業執行關機 (SQL Server Management Studio) | Microsoft Docs"
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
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: df7d516501546d36ac3fac900d694e1e32e2f336
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>設定作業執行關機 (SQL Server Management Studio)
此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]，在 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] 中設定 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 等待執行中作業完成的等候時間，之後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 便會自行結束。  
  
**本主題內容**  
  
-   **開始之前：**  
  
    [Security](#Security)  
  
-   **若要使用下列項目設定 SQL Server Agent 作業的關機時間：**  
  
    [Transact-SQL](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>開始之前  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
根據預設， **系統管理員 (sysadmin)** 固定伺服器角色的成員可以設定 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 等待執行中作業完成的等候時間，之後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 便會自行結束。 其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
## <a name="SSMSProcedure"></a>使用 SQL Server Management Studio  
  
#### <a name="to-set-job-execution-shutdown"></a>若要設定作業執行關機  
  
1.  在 **[物件總管]** 中，按一下加號，展開要設定作業執行關機間隔的伺服器。  
  
2.  以滑鼠右鍵按一下 [SQL Server Agent]，然後選取 [屬性]。  
  
3.  在 **[選取頁面]**底下，選取 **[作業的系統]**。  
  
4.  設定 [關機逾時間隔] (以秒為單位)，以增加或減少關機的逾時間隔。 這決定了在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 自行結束前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 會等待執行中作業完成的時間。  
  

