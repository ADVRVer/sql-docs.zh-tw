---
title: "建立 WMI 事件警示 | Microsoft Docs"
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
- WMI event alerts [SQL Server Management Studio]
ms.assetid: b8c46db6-408b-484e-98f0-a8af3e7ec763
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 97694f2029532a172f0b0f895dfc95ebc5a8a729
ms.lasthandoff: 04/11/2017

---
# <a name="create-a-wmi-event-alert"></a>建立 WMI 事件警示
此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] 中建立在伺服器事件的 WMI 提供者所監視的特定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] 事件發生時，所引發的 [!INCLUDE[tsql](../../includes/tsql_md.md)]Agent 警示。  
  
如需使用 WMI 提供者監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 事件的詳細資訊，請參閱 [伺服器事件類別和屬性的 WMI 提供者](http://msdn.microsoft.com/en-us/80767fe0-32ac-406a-81a0-8212cd6ce7e4)。 如需接收 WMI 事件警示通知所需權限的詳細資訊，請參閱 [選取 SQL Server Agent 服務的帳戶](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md)。 如需 WQL 的詳細資訊，請參閱 [搭配伺服器事件的 WMI 提供者使用 WQL](http://msdn.microsoft.com/en-us/58b67426-1e66-4445-8e2c-03182e94c4be)。  
  
**本主題內容**  
  
-   **開始之前：**  
  
    [限制事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **若要使用下列項目建立 WMI 事件警示：**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>開始之前  
  
### <a name="Restrictions"></a>限制事項  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] 提供了一種簡單的圖形方式供您管理整個警示系統，建議您利用這個方式來設定警示基礎結構。  
  
-   **xp_logevent** 產生的事件出現在 master 資料庫中。 因此，除非警示的 **xp_logevent** 是 **@database_name** 或 NULL，否則， **xp_logevent** 不會觸發警示。  
  
-   僅支援執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 之電腦上的 WMI 命名空間。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行 **sp_add_alert**。  
  
## <a name="SSMSProcedure"></a>使用 SQL Server Management Studio  
  
#### <a name="to-create-a-wmi-event-alert"></a>若要建立 WMI 事件警示  
  
1.  在 **[物件總管]** 中，按一下加號以展開您要建立 WMI 事件警示的伺服器。  
  
2.  按一下加號展開 **[SQL Server Agent]**。  
  
3.  以滑鼠右鍵按一下 **[警示]** ，然後選取 **[新增警示]**。  
  
4.  在 **[新增警示]** 對話方塊中的 **[名稱]** 方塊，輸入此警示的名稱。  
  
5.  選取 **[啟用]** 核取方塊以讓警示得以執行。 根據預設，會選取 **[啟用]** 。  
  
6.  在 **[類型]** 清單中，選取 **[WMI 事件警示]**。  
  
7.  在 [WMI 事件警示定義] 底下的 [命名空間] 方塊中，指定 WMI 查詢語言 (WQL) 陳述式的 WMI 命名空間，以識別哪個 WMI 事件將會觸發此警示。  
  
8.  在 **[查詢]** 方塊中，指定會識別警示所回應之事件的 WQL 陳述式。  
  
9. 按一下 **[確定]**。  
  
## <a name="TsqlProcedure"></a>使用 Transact-SQL  
  
#### <a name="to-create-a-wmi-event-alert"></a>若要建立 WMI 事件警示  
  
1.  在 **[物件總管]**中，連接到 [!INCLUDE[ssDE](../../includes/ssde_md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 [執行] 。  
  
    ```  
    -- creates a WMI event alert that retrieves all event properties for any ALTER_TABLE event that occurs on table AdventureWorks2012.Sales.SalesOrderDetail  
    -- This example assumes that the message 54001 already exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert 2',  
        @message_id = 54001  
        @notification_message = N'Error 54001 has occurred on the Sales.SalesOrderDetail table on the AdventureWorks2012 database.',  
        @wmi_namespace = '\\.\root\Microsoft\SqlServer\ServerEvents\,  
        @wmi_query = N'SELECT * FROM ALTER_TABLE   
    WHERE DatabaseName = 'AdventureWorks2012' AND SchemaName = 'Sales'   
        AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'';  
    GO  
    ```  
  
如需詳細資訊，請參閱 [sp_add_alert (Transact-SQL)](http://msdn.microsoft.com/en-us/d9b41853-e22d-4813-a79f-57efb4511f09)。  
  

