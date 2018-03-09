---
title: "設定 AlwaysOn 可用性群組的 SQL Server 執行個體 | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], about
ms.assetid: fad8db32-593e-49d5-989c-39eb8399c416
caps.latest.revision: "18"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ee7f1d762943a92600257e6043568f9700aab0ce
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2018
---
# <a name="configuration-of-a-server-instance-for-always-on-availability-groups-sql-server"></a>設定 AlwaysOn 可用性群組的伺服器執行個體 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  本主題包含在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中設定 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 執行個體以支援 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]之需求的相關資訊。  
  
> [!IMPORTANT]  
>  如需 Windows Server 容錯移轉叢集 (WSFC) 節點和 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 執行個體之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]必要條件與限制的基本資訊，請參閱 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)之需求的相關資訊。  
  
 **本主題內容：**  
  
-   [詞彙和定義](#TermsAndDefinitions)  
  
-   [設定伺服器執行個體，以支援 AlwaysOn 可用性群組](#ConfigSI)  
  
-   [相關工作](#RelatedTasks)  
  
-   [相關內容](#RelatedContent)  
  
##  <a name="TermsAndDefinitions"></a> 詞彙和定義  
 [AlwaysOn 可用性群組](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
 提供企業級資料庫鏡像替代方案的高可用性與災害復原解決方案。 *「可用性群組」* (Availability Group) 支援一組可一起容錯移轉之離散化使用者資料庫的容錯移轉環境，也就是所謂的 *「可用性資料庫」*(Availability Database)。  
  
 「可用性複本」  
 特定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體所裝載之可用性群組的具現化，其中維護屬於可用性群組之每個可用性資料庫的本機副本。 有兩種類型的可用性複本存在：單一 *「主要複本」* (Primary Replica) 以及一到四個 *「次要複本」*(Secondary Replica)。 針對給定可用性群組裝載可用性複本的伺服器執行個體必須位於單一 Windows Server 容錯移轉叢集 (WSFC) 叢集的不同節點上。  
  
 [資料庫鏡像端點](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
 端點是 SQL Server 物件，可讓 SQL Server 在網路上進行通訊。 若要參與資料庫鏡像及/或 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ，伺服器執行個體需要特殊的專用端點。 伺服器執行個體上的所有鏡像和可用性群組連接都會使用相同的資料庫鏡像端點。 這個端點是特殊目的之端點，專門用來接收其他伺服器執行個體的這些連接。  
  
##  <a name="ConfigSI"></a> 設定伺服器執行個體，以支援 AlwaysOn 可用性群組  
 若要支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]，伺服器執行個體必須位於裝載可用性群組之 WSFC 容錯移轉叢集中的節點、已啟用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ，而且擁有資料庫鏡像端點。  
  
1.  在要參與一個或多個可用性群組的每一個伺服器執行個體上啟用 AlwaysOn 可用性群組功能。 給定伺服器執行個體只能裝載給定可用性群組的單一可用性複本。  
  
2.  確定伺服器執行個體擁有資料庫鏡像端點。  
  
##  <a name="RelatedTasks"></a> 相關工作  
 **啟用 AlwaysOn 可用性群組**  
  
-   [啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **若要判斷資料庫鏡像端點是否存在**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)  
  
 **若要建立資料庫鏡像端點**  
  
-   [針對 AlwaysOn 可用性群組建立資料庫鏡像端點 &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
##  <a name="RelatedContent"></a> 相關內容  
  
-   **部落格：**  
  
     [Always On - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases (AlwaysOn - HADRON 學習系列：資料庫啟用 HADRON 時工作者集區的使用方式)](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
     [CSS SQL Server 工程師部落格](http://blogs.msdn.com/b/psssql/)  
  
-   **影片：**  
  
     [Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution (Microsoft SQL Server 代碼 "Denali" AlwaysOn 系列第一部分：新一代高可用性解決方案簡介)](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Code-Named "Denali" Always On Series,Part 2: Building a Mission-Critical High Availability Solution Using Always On (Microsoft SQL Server 代碼 "Denali" AlwaysOn 系列第二部分：使用 AlwaysOn 建立任務關鍵性高可用性解決方案)](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **白皮書：**  
  
     [Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft 的 SQL Server 2012 白皮書](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server 客戶諮詢團隊白皮書](http://sqlcat.com/)  
  
## <a name="see-also"></a>另請參閱  
 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)   
 [資料庫鏡像端點 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [AlwaysOn 可用性群組︰互通性 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)   
 [容錯移轉叢集和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [SQL Server 的 Windows Server 容錯移轉叢集 &#40;WSFC&#41;](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [AlwaysOn 容錯移轉叢集執行個體 &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
  
