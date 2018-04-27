---
title: 檢視 SQL Server Agent 錯誤記錄檔 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- viewing SQL Server Agent error logs
- displaying SQL Server Agent error logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: de920425-fa44-469f-b83d-49e3f97e97f4
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cccff0d92ffc1edfc7ba15a04eb0bb93ec531649
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="view-sql-server-agent-error-log-sql-server-management-studio"></a>View SQL Server Agent Error Log (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支援多數 (但非全部) 的 SQL Server Agent 功能。 如需詳細資料，請參閱 [Azure SQL Database 受控執行個體與 SQL Server 之間的 T-SQL 差異](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

此主題描述如何使用  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] 中檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]Agent 錯誤記錄檔。  
  
記錄檔檢視器會顯示許多不同元件的記錄資訊。 當記錄檔檢視器開啟時，使用 **[選取記錄]** 窗格以選取您要顯示的記錄檔。 每個記錄檔都會顯示適用於該記錄檔類型的資料行。 可用的記錄檔取決於記錄檔檢視器的開啟方式而定。  
  
**本主題內容**  
  
-   **開始之前：**  
  
    [限制事項](#Restrictions)  
  
    [Security](#Security)  
  
-   [若要使用 SQL Server Management Studio 檢視 SQL Server Agent 錯誤記錄檔](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>開始之前  
  
### <a name="Restrictions"></a>限制事項  
只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)](系統管理員) 固定伺服器角色的成員。 此帳戶必須擁有下列 Windows 權限：  
  
-   以服務登入 (SeServiceLogonRight)  
  
-   取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)  
  
-   略過跨越檢查 (SeChangeNotifyPrivilege)  
  
-   調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)  
  
如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 服務帳戶所需的 Windows 權限詳細資訊，請參閱 [選取 SQL Server Agent 服務的帳戶](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 和 [設定 Windows 服務帳戶](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)。  
  
## <a name="SSMSProcedure"></a>使用 SQL Server Management Studio  
  
#### <a name="to-view-the-includessnoversionincludesssnoversionmdmd-agent-error-log"></a>若要檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 錯誤記錄檔  
  
1.  在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含要檢視的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 錯誤記錄檔。  
  
2.  按一下加號展開 **[SQL Server Agent]**。  
  
3.  按一下加號展開 **[錯誤記錄檔]** 資料夾。  
  
4.  以滑鼠右鍵按一下要檢視的錯誤記錄檔，然後選取 [檢視代理程式記錄]。  
  
    [記錄檔檢視器 - <伺服器名稱>] 對話方塊有下列選項：  
  
    **載入記錄**  
    開啟對話方塊供您指定所要載入的記錄檔。  
  
    **匯出**  
    開啟對話方塊，以讓您將 [記錄檔摘要] 格線中所顯示的資訊匯出至文字檔。  
  
    **[重新整理]**  
    重新整理所選取之記錄檔的檢視。 當套用任何篩選設定時， **[重新整理]** 按鈕會從目標伺服器重新讀取選取的記錄檔。  
  
    **篩選**  
    開啟對話方塊，以讓您指定用來篩選記錄檔的設定，例如 [連接]、[日期] 或其他的 [一般] 篩選準則。  
  
    **搜尋**  
    搜尋記錄檔中的特定文字。 不支援使用萬用字元搜尋。  
  
    **停止**  
    停止載入記錄檔項目。 例如，如果遠端或離線記錄檔需要長時間才能載入，而您只要檢視最新項目時，就可以使用這個選項。  
  
    **記錄檔摘要**  
    此資訊面板會顯示記錄檔篩選的摘要。 如果未篩選檔案，則會看到下列文字： **[未套用篩選]**。 如果篩選已套用到記錄檔，則會看到下列文字：**篩選記錄項目的準則:**<filter criteria>。  
  
    **選取的資料列詳細資料**  
    選取資料列以顯示頁面下方有關選取之事件資料列的其他詳細資料。 將資料行拖曳至方格中的新位置，以重新排序資料行。 將方格標頭中的資料行分隔線拖曳至左邊或右邊，以調整資料行大小。 在方格標頭中按兩下資料行分隔線，自動將資料行大小調整為內容寬度。  
  
    **執行個體**  
    發生事件之執行個體的名稱。 顯示為 *&lt;電腦名稱*\\*執行個體名稱&gt;*。  
  
    **Date**  
    顯示事件的日期。  
  
    **Source**  
    顯示事件建立的來源功能，例如服務名稱 (如 MSSQLSERVER)。 不是所有記錄檔類型都會出現來源。  
  
    **訊息**  
    顯示與事件相關聯的任何訊息。  
  
    **記錄類型**  
    顯示事件所屬之記錄檔的類型。 所有選取的記錄檔都會出現在記錄檔摘要視窗中。  
  
    **記錄來源**  
    顯示擷取事件之來源記錄的描述。  
  
5.  完成後，請按一下 **[關閉]**。  
  
