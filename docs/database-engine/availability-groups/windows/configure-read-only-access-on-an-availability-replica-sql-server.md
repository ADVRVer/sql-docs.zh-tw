---
title: "設定可用性複本上的唯讀存取 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "可用性複本的連接存取"
  - "可用性群組 [SQL Server], 可讀取次要複本"
  - "使用中次要複本 [SQL Server], 唯讀存取"
  - "可用性群組 [SQL Server], 唯讀路由"
  - "可用性群組 [SQL Server], 用戶端連接性"
ms.assetid: 22387419-22c4-43fa-851c-5fecec4b049b
caps.latest.revision: 35
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 35
---
# 設定可用性複本上的唯讀存取 (SQL Server)
  預設允許與主要複本之間的讀寫和讀取意圖的存取，但是不允許連接 AlwaysOn 可用性群組的次要複本。 本主題說明如何藉由使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell，針對 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中 AlwaysOn 可用性群組的可用性複本設定連接存取。  
  
 如需針對次要複本啟用唯讀存取的含意資訊，以及連接存取簡介，請參閱[關於可用性複本的用戶端連接存取 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)和[使用中次要：可讀取的次要複本 &#40;AlwaysOn 可用性群組&#41;](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。  
  
-   **開始之前：**  
  
     [必要條件和限制](#Prerequisites)  
  
     [安全性](#Security)  
  
-   **若要使用下列項目設定可用性複本的存取：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **後續操作：**[針對可用性複本設定唯讀存取之後](#FollowUp)  
  
-   [相關工作](#RelatedTasks)  
  
-   [相關內容](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Prerequisites"></a> 必要條件和限制  
  
-   若要設定不同的連接存取，您必須連接到裝載主要複本的伺服器執行個體。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
  
|工作|Permissions|  
|----------|-----------------|  
|若要在建立可用性群組時設定複本|需要 **sysadmin** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。|  
|若要修改可用性複本|需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。|  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 **若要設定可用性複本的存取**  
  
1.  在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。  
  
2.  依序展開 [AlwaysOn 高可用性] 節點和 [可用性群組] 節點。  
  
3.  按一下要變更複本的可用性群組。  
  
4.  以滑鼠右鍵按一下可用性複本，然後按一下 [屬性]。  
  
5.  在 **[可用性複本屬性]** 對話方塊中，可以變更主要角色和次要角色的連接存取，如下所示：  
  
    -   如果是次要角色，請從 **[可讀取次要]** 下拉清單中選擇一個新值，如下所示：  
  
         **否**  
         不允許使用者連接至這個複本的次要資料庫。 無法讀取這些資料庫。 這是預設值。  
  
         **僅限讀取意圖**  
         只允許與這個複本的次要資料庫進行唯讀連接。 可以讀取所有次要資料庫。  
  
         **是**  
         允許與這個複本的次要資料庫之間的所有連接，但只供讀取存取。 可以讀取所有次要資料庫。  
  
    -   如果是主要角色，請從 **[主要角色的連接模式]** 下拉清單中選擇一個新值，如下所示：  
  
         **允許所有連接**  
         主要複本的資料庫允許所有連接。 這是預設值。  
  
         **允取讀取/寫入連接**  
         當 Application Intent 屬性設為 **ReadWrite** 或是未設定 Application Intent 連接屬性時，便會允許連接。 不允許 Application Intent 連接屬性設為 **ReadOnly** 的連接。 這有助於防止客戶錯誤地將讀取意圖的工作負載連接至主要複本。 如需有關 Application Intent 連接屬性的詳細資訊，請參閱＜ [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)＞。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **若要設定可用性複本的存取**  
  
> [!NOTE]  
>  如需這個程序的範例，請參閱本節稍後的[範例 &#40;Transact-SQL&#41;](#TsqlExample)。  
  
1.  連接到裝載主要複本的伺服器執行個體。  
  
2.  如果您要針對新的可用性群組指定複本，請使用 [CREATE AVAILABILITY GROUP](../../../t-sql/statements/create-availability-group-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式。 如果您要加入或修改現有可用性群組的複本，請使用 [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式。  
  
    -   若要設定次要角色的連接存取，請在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 SECONDARY_ROLE 選項，如下所示：  
  
         SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**  
  
         其中  
  
         NO  
         不允許直接連接這個複本的次要資料庫。 無法讀取這些資料庫。 這是預設值。  
  
         READ_ONLY  
         只允許與這個複本的次要資料庫進行唯讀連接。 可以讀取所有次要資料庫。  
  
         ALL  
         允許與這個複本的次要資料庫之間的所有連接，但只供讀取存取。 可以讀取所有次要資料庫。  
  
3.  若要設定主要角色的連接存取，請在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 PRIMARY_ROLE 選項，如下所示：  
  
     PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**  
  
     其中  
  
     READ_WRITE  
     不允許 Application Intent 連接屬性設為 **ReadOnly** 的連接。  當 Application Intent 屬性設為 **ReadWrite** 或是未設定 Application Intent 連接屬性時，便會允許連接。 如需有關 Application Intent 連接屬性的詳細資訊，請參閱＜ [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)＞。  
  
     ALL  
     主要複本的資料庫允許所有連接。 這是預設值。  
  
###  <a name="TsqlExample"></a> 範例 (Transact-SQL)  
 下列範例會將次要複本加入名為 *AG2*的可用性群組。 接著指定一個獨立伺服器執行個體 *COMPUTER03\HADR_INSTANCE*，以裝載新的可用性複本。 將此複本設定為只允許主要角色的讀寫連接以及只允許次要角色的讀取意圖連接。  
  
```  
ALTER AVAILABILITY GROUP AG2   
   ADD REPLICA ON   
      'COMPUTER03\HADR_INSTANCE' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:7022',  
         PRIMARY_ROLE ( ALLOW_CONNECTIONS = READ_WRITE ),  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY )  
         );   
GO  
```  
  
##  <a name="PowerShellProcedure"></a> 使用 PowerShell  
 **若要設定可用性複本的存取**  
  
> [!NOTE]  
>  如需程式碼範例，請參閱本節稍後的[範例 (PowerShell)](#PSExample)。  
  
1.  將目錄 (**cd**) 變更為裝載主要複本的伺服器執行個體。  
  
2.  將可用性複本加入可用性群組中時，請使用 **New-SqlAvailabilityReplica** Cmdlet。 修改現有的可用性複本時，請使用 **Set-SqlAvailabilityReplica** Cmdlet。 相關參數如下所示：  
  
    -   若要設定次要角色的連接存取，請指定 **ConnectionModeInSecondaryRole***secondary_role_keyword* 參數，其中 *secondary_role_keyword* 等於下列值之一︰  
  
         **AllowNoConnections**  
         不允許直接連接次要複本的資料庫，這些資料庫也不可用於讀取存取。 這是預設值。  
  
         **AllowReadIntentConnectionsOnly**  
         次要複本的資料庫只允許 Application Intent 屬性設為 **ReadOnly** 的連接。 如需有關這個屬性的詳細資訊，請參閱＜ [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)＞。  
  
         **AllowAllConnections**  
         次要複本的資料庫允許所有連接進行唯讀存取。  
  
    -   若要設定主要角色的連接存取，請指定 **ConnectionModeInPrimaryRole***primary_role_keyword* 參數，其中 *primary_role_keyword* 等於下列值之一︰  
  
         **AllowReadWriteConnections**  
         不允許 Application Intent 連接屬性設為 ReadOnly 的連接。 當 Application Intent 屬性設為 ReadWrite 或是未設定 Application Intent 連接屬性時，便會允許連接。 如需有關 Application Intent 連接屬性的詳細資訊，請參閱＜ [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)＞。  
  
         **AllowAllConnections**  
         主要複本的資料庫允許所有連接。 這是預設值。  
  
    > [!NOTE]  
    >  若要檢視 Cmdlet 的語法，請在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell 環境中使用 **Get-Help** Cmdlet。 如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)。  
  
 **若要設定和使用 SQL Server PowerShell 提供者**  
  
-   [SQL Server PowerShell 提供者](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
###  <a name="PSExample"></a> 範例 (PowerShell)  
 下列範例將 **ConnectionModeInSecondaryRole** 和 **ConnectionModeInPrimaryRole** 參數設定為 **AllowAllConnections**。  
  
```  
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
Set-SqlAvailabilityReplica -ConnectionModeInSecondaryRole "AllowAllConnections" `   
-InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ConnectionModeInPrimaryRole "AllowAllConnections" `   
-InputObject $primaryReplica  
  
```  
  
##  <a name="FollowUp"></a> 後續操作：針對可用性複本設定唯讀存取之後  
 **可讀取的次要複本的唯讀存取**  
  
-   當您使用 [bcp 公用程式](../../../tools/bcp-utility.md)或 [sqlcmd 公用程式](../../../tools/sqlcmd-utility.md)時，您可以藉由指定 **-K ReadOnly** 參數，為啟用唯讀存取的任何次要複本指定唯讀存取。  
  
-   若要啟用用戶端應用程式以連接到可讀取的次要副本：  
  
    ||必要條件|連結|  
    |-|------------------|----------|  
    |![Checkbox](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|確定可用性群組擁有接聽程式。|[建立或設定可用性群組接聽程式 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)|  
    |![Checkbox](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|設定可用性群組的唯讀路由。|[設定可用性群組的唯讀路由 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)|  
  
 **容錯移轉之後可能會影響觸發程序和作業的因素**  
  
 如果您的觸發程序和作業在非可讀取的次要資料庫或可讀取的次要資料庫上執行時會失敗，則需要撰寫觸發程序和作業的指令碼來檢查特定複本，判斷資料庫是主要資料庫或是可讀取的次要資料庫。 若要取得這項資訊，請使用 [DATABASEPROPERTYEX](../../../t-sql/functions/databasepropertyex-transact-sql.md) 函數傳回資料庫的 **Updatability** 屬性。 若要識別唯讀資料庫，請指定 READ_ONLY 做為值，如下所示：  
  
```  
DATABASEPROPERTYEX([db name],’Updatability’) = N’READ_ONLY’  
```  
  
 若要識別讀寫資料庫，請指定 READ_WRITE 做為值。  
  
##  <a name="RelatedTasks"></a> 相關工作  
  
-   [設定可用性群組的唯讀路由 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [建立或設定可用性群組接聽程式 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
##  <a name="RelatedContent"></a> 相關內容  
  
-   [AlwaysOn：可讀取次要功能的價值主張](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On-value-proposition-of-readable-secondary.aspx)  
  
-   [AlwaysOn：為何有兩個選項可針對讀取工作負載啟用次要複本？](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On-why-there-are-two-options-to-enable-a-secondary-replica-for-read-workload.aspx)  
  
-   [AlwaysOn：設定可讀取次要複本](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On-setting-up-readable-seconary-replica.aspx)  
  
-   [AlwaysOn：我剛剛啟用可讀取次要功能，但我的查詢被封鎖？](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On-i-just-enabled-readble-secondary-but-my-query-is-blocked.aspx)  
  
-   [AlwaysOn：在可讀取次要、唯讀資料庫和資料庫快照集上提供最新的統計資料](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On-making-upto-date-statistics-available-on-readable-secondary-read-only-database-and-database-snapshot.aspx)  
  
-   [AlwaysOn：唯讀資料庫、資料庫快照集和次要複本上的統計資料挑戰](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On-challenges-with-statistics-on-readonly-database-database-snapshot-and-secondary-replica.aspx)  
  
-   [AlwaysOn：在次要複本上執行報表工作負載時，對主要工作負載的影響](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On-impact-on-the-primary-workload-when-you-run-reporting-workload-on-the-secondary-replica.aspx)  
  
-   [AlwaysOn：將可讀取次要項目上的報表工作負載對應至快照集隔離的影響](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On-impact-of-mapping-reporting-workload-to-snapshot-isolation-on-readable-secondary.aspx)  
  
-   [AlwaysOn：在次要複本上執行報表工作負載時，將 REDO 執行緒封鎖降至最低](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On-minimizing-blocking-of-redo-thread-when-running-reporting-workload-on-secondary-replica.aspx)  
  
-   [AlwaysOn：可讀取次要功能和資料延遲](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/Always%20On.aspx)  
  
## 另請參閱  
 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [使用中次要：可讀取的次要複本 &#40;AlwaysOn 可用性群組&#41;](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [關於可用性複本的用戶端連接存取 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)  
  
  