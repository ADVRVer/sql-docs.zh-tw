---
title: 建立及設定可用性群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], creating
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9858638287876d31733035d1a6bb6d95705708f
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228723"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a>建立及設定可用性群組 (SQL Server)
  本章節的主題將說明如何在位於單一 WSFC 容錯移轉叢集內不同 Windows Server 容錯移轉叢集 (WSFC) 節點上的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 執行個體上部署 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 實作。  
  
 建立第一個可用性群組之前，我們建議您先熟悉下列主題中的資訊：  
  
 [AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
 此主題描述電腦、WSFC 節點、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體、可用性群組、複本和資料庫的必要條件、限制和建議。 此主題也包含安全性考量的資訊。  
  
 [具有 AlwaysOn 可用性群組 &#40;SQL Server 的消費者入門&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
 包含下列作業的步驟資訊：設定伺服器執行個體、建立可用性群組、設定用戶端連接的可用性群組、管理可用性群組，以及監視可用性群組。  
  
 
  
##  <a name="RelatedTasks"></a>相關工作  
 **若要設定的伺服器實例[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**  
  
-   [啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [建立適用于 Windows 驗證的資料庫鏡像端點 &#40;Transact-sql&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [允許資料庫鏡像端點使用 &#40;Transact-sql 的輸出連接憑證&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 **開始使用設定 AlwaysOn 可用性群組**  
  
-   [具有 AlwaysOn 可用性群組 &#40;SQL Server 的消費者入門&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 **若要建立及設定新的可用性群組**  
  
-   [使用可用性群組 Wizard &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [&#40;Transact-sql 建立可用性群組&#41;](create-an-availability-group-transact-sql.md)  
  
-   [建立可用性群組 &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [使用 [新增可用性群組] 對話方塊 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [建立或設定可用性群組接聽程式 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [設定彈性容錯移轉原則以控制自動容錯移轉的條件 (AlwaysOn 可用性群組)](configure-flexible-automatic-failover-policy.md)  
  
-   [在可用性複本上設定備份 &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [設定可用性複本上的唯讀存取 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [設定可用性群組的唯讀路由 &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [在 AlwaysOn 次要資料庫上啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [管理可用性群組之資料庫的登入和作業 &#40;SQL Server&#41;](../../logins-and-jobs-for-availability-group-databases.md)  
  
 **疑難排解**  
  
-   [針對已刪除 AlwaysOn 可用性群組設定（SQL Server）進行疑難排解](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [針對失敗的新增檔案作業進行疑難排解 &#40;AlwaysOn 可用性群組&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a>相關內容  
  
-   **網路**  
  
     [AlwaysON - HADRON 學習系列：具備 HADRON 功能之資料庫的工作者集區使用方式](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server 工程師 Blog](https://blogs.msdn.com/b/psssql/)  
  
-   **視頻**  
  
     [Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 1 部：新一代高可用性解決方案簡介](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 2 部：使用 AlwaysOn 建立關鍵任務的高可用性方案](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **白皮書**  
  
     [Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [適用于 SQL Server 2012 的 Microsoft 技術白皮書](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server 客戶諮詢小組白皮書](http://sqlcat.com/)  
  
## <a name="see-also"></a>另請參閱  
 [AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [管理可用性群組 &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)   
 [AlwaysOn 可用性群組（SQL Server）操作問題的 AlwaysOn 原則](always-on-policies-for-operational-issues-always-on-availability.md)   
 [監視可用性群組 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [AlwaysOn 可用性群組：互通性 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)  
  
