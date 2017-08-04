---
title: "對使用者授與 DQS 角色 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 805020ab366ec0e993c8f4be54a4d18a22510911
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="grant-dqs-roles-to-users"></a>對使用者授與 DQS 角色
  本主題描述如何根據 Windows 主體建立 SQL 登入，並在 DQS_MAIN 資料庫上授與 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 角色。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須執行 DQSInstaller.exe 檔案，才可以完成 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 的安裝。 如需詳細資訊，請參閱 [執行 DQSInstaller.exe 完成 Data Quality Server 安裝](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。  
  
-   您的 Windows 使用者帳戶必須是適當固定伺服器角色 (例如 securityadmin、serveradmin 或 sysadmin) 的成員，才能建立 SQL 登入並授與它們 DQS 角色。  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a>若要建立 SQL 登入並授與 DQS 角色  
  
1.  啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。  
  
2.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展開您的 SQL Server 執行個體，然後展開 **[安全性]**。  
  
3.  以滑鼠右鍵按一下 [安全性] 資料夾，並指向 [新增]，然後按一下 [登入]。  
  
4.  在 **[登入 - 新增]** 對話方塊的 **[登入名稱]** 方塊中，指定 Windows 使用者的名稱，指定 **[Windows 驗證]**做為驗證類型，然後按一下 **[搜尋]** 驗證使用者。  
  
5.  使用者驗證完成後，按一下左窗格中的 **[使用者對應]** 頁面。  
  
6.  根據使用者所需的存取層級，在右邊的窗格中，從 **DQS_MAIN** 資料庫的 [地圖] 資料行選取該核取方塊，然後選取 [資料庫角色成員資格對象: DQS_MAIN] 窗格中的 **dqs_administrator**、**dqs_kb_editor** 或 **dqs_kb_operator** 核取方塊。 如需有關三個 DQS 角色的詳細資訊，請參閱＜ [DQS Security](../../data-quality-services/dqs-security.md)＞。  
  
7.  在 **[登入 - 新增]** 對話方塊中，按一下 **[確定]** 套用變更。  
  
    > [!NOTE]  
    >  如果您對使用者授與 **dqs_administrator** 角色並套用了變更，然後重新檢查使用者的權限，也會同時選取另外兩個 DQS 角色核取方塊 (**dq_kb_editor** 和 **dqs_kb_operator**)。  
  
## <a name="next-steps"></a>後續步驟  
 嘗試使用您剛才為其建立 SQL 登入並授與 DQS 角色的 Windows 使用者帳戶登入 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 。  
  
## <a name="see-also"></a>另請參閱  
 [安裝 Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [建立登入](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
