---
title: 為失敗的新增檔案作業進行疑難排解 (AlwaysOn 可用性群組) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 253866dc7483fb74162a55dc4f4c376c7b630312
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66803479"
---
# <a name="troubleshoot-a-failed-add-file-operation-always-on-availability-groups"></a>疑難排解失敗的加入檔案作業 (AlwaysOn 可用性群組)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  在某些 AlwaysOn 可用性群組部署中，在裝載主要複本的系統和裝載次要複本的系統之間會有檔案路徑差異。 如果加入檔案作業的檔案路徑不存在於次要複本，則加入檔案作業將會在主要資料庫上成功完成。 但是加入檔案作業會造成次要資料庫暫停。 而這又會導致次要複本進入 NOT SYNCHRONIZING 狀態。  
  
> [!NOTE]  
>  我們建議，給定次要資料庫的檔案路徑 (包括磁碟機代號) 盡可能與對應主要資料庫的路徑完全相同。  
  
## <a name="problem-resolution"></a>問題解決  
 若要解決此問題，資料庫擁有者必須完成以下步驟：  
  
1.  從可用性群組中移除次要資料庫。 如需詳細資訊，請參閱[將次要資料庫從可用性群組移除 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-a-secondary-database-from-an-availability-group-sql-server.md)。  
  
2.  在現有次要資料庫上，使用 WITH NORECOVERY 和 WITH MOVE (指定裝載次要複本之伺服器執行個體上的檔案路徑)，將包含加入之檔案的檔案群組的完整備份還原到次要資料庫。 如需詳細資訊，請參閱[將資料庫還原到新位置 &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)。  
  
3.  在主要伺服器上備份包含加入檔案作業的交易記錄，並且使用 WITH NORECOVERY 和 WITH MOVE 手動在次要資料庫上還原記錄備份。  
  
4.  透過使用 WITH NO RECOVERY 從主要資料庫還原任何其他未完成的記錄備份，準備次要資料庫重新加入可用性群組。  
  
5.  將次要資料庫重新加入可用性群組。 如需詳細資訊，請參閱 [將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)   
 [孤立的使用者疑難排解 &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [疑難排解 AlwaysOn 可用性群組組態 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)
