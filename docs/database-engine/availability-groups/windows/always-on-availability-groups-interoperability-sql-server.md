---
title: "AlwaysOn 可用性群組：互通性 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 04/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
caps.latest.revision: "21"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2568fdee9fa349b1f3590d1a0e9cc31fd4b5191d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>AlwaysOn 可用性群組：互通性 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  本主題記錄 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中其他 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]功能的互通性。  
  
##  <a name="Interop"></a> 與 AlwaysOn 可用性群組互通的功能  
 下表列出與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 互通的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]功能。 **[詳細資訊]** 資料行中的連結表示有適用於所指功能的互通性考量。  
  
|功能|[詳細資訊]|  
|-------------|----------------------|  
|異動資料擷取|[複寫、變更追蹤、異動資料擷取和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/replicate-track-change-data-capture-always-on-availability.md)|  
|變更追蹤|[複寫、變更追蹤、異動資料擷取和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/replicate-track-change-data-capture-always-on-availability.md)|  
|自主資料庫|[自主資料庫與 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/contained-databases-with-always-on-availability-groups-sql-server.md)|  
|資料庫加密|[加密的資料庫與 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|資料庫快照集|[資料庫快照集與 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM 與 FileTable|[FILESTREAM 和 FileTable 與 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|全文檢索搜尋|注意：全文檢索索引與 AlwaysOn 次要資料庫同步。|  
|記錄傳送|[從記錄傳送遷移至 AlwaysOn 可用性群組的必要條件 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|遠端 Blob 存放區 (RBS)|[遠端 Blob 存放區 &#40;RBS&#41; 及 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|複寫|[設定 AlwaysOn 可用性群組的複寫 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [維護 AlwaysOn 發行集資料庫 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [複寫、變更追蹤、異動資料擷取和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [複寫訂閱者及 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Analysis Services|[Analysis Services 與 AlwaysOn 可用性群組](../../../database-engine/availability-groups/windows/analysis-services-with-always-on-availability-groups.md)|  
|Reporting Services|利用唯讀次要複本做為報表資料來源，減少主要讀寫複本上的負載。<br /><br /> [使用 AlwaysOn 可用性群組的 Reporting Services &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Service Broker|[使用 AlwaysOn 可用性群組的 Service Broker &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md)|  
|SQL Server Agent||  
  
##  <a name="restrictions"></a> 與 AlwaysOn 可用性群組相互溝通的功能限制  
 下列可與 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 相互溝通的功能有特定限制。 如需詳細資訊，請參閱連結主題。  
  
-   跨資料庫交易/分散式交易 ([!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] 和 Windows Server 2016)。 如需詳細資訊，請參閱 [AlwaysOn 可用性群組和資料庫鏡像的跨資料庫交易和分散式交易 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)  
  
##  <a name="NoInterop"></a> 不與 AlwaysOn 可用性群組互通的功能  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 無法與下列功能互通：  
  
-   資料庫鏡像。 如需詳細資訊，請參閱[資料庫鏡像或 AlwaysOn 可用性群組不支援跨資料庫交易 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)。  
  
##  <a name="RelatedContent"></a> 相關內容  
  
-   **部落格：**  
  
     [移轉指南：從先前叢集和鏡像部署移轉至 SQL Server 2012 容錯移轉叢集和可用性群組](https://blogs.msdn.microsoft.com/sqlalwayson/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments/)  
  
     [SQL Server AlwaysOn 團隊部落格：SQL Server AlwaysOn 官方團隊部落格](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
     [CSS SQL Server 工程師部落格](http://blogs.msdn.com/b/psssql/)  
  
-   **白皮書：**  
  
     [移轉指南：從結合資料庫鏡像與記錄傳送的先前部署遷移至 AlwaysOn 可用性群組](http://msdn.microsoft.com/library/jj635217)  
  
     [Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft 的 SQL Server 2012 白皮書](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server 客戶諮詢團隊白皮書](http://sqlcat.com/)  
  
## <a name="see-also"></a>另請參閱  
 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Always On 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
