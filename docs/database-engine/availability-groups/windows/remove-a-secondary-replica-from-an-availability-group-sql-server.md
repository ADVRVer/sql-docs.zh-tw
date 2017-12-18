---
title: "將次要複本從可用性群組移除 (SQL Server) | Microsoft Docs"
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
f1_keywords: sql13.swb.availabilitygroup.removesecondaryar.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 35ddc8b6-3e7c-4417-9a0a-d4987a09ddf7
caps.latest.revision: "38"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 58accac84c6516967231b8c0803afe569689d069
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="remove-a-secondary-replica-from-an-availability-group-sql-server"></a>將次要複本從可用性群組移除 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell，在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中將次要複本從 AlwaysOn 可用性群組中移除。  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [必要條件](#Prerequisites)  
  
     [安全性](#Security)  
  
-   **若要使用下列項目移除次要複本：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **後續操作：**[移除次要複本之後](#PostBestPractices)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   只有在主要複本上才支援這個工作。  
  
-   只有次要複本可以從可用性群組中移除。  
  
###  <a name="Prerequisites"></a> 必要條件  
  
-   您必須連接到裝載可用性群組之主要複本的伺服器執行個體。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 **若要移除次要複本**  
  
1.  在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。  
  
2.  依序展開 [AlwaysOn 高可用性] 節點和 [可用性群組] 節點。  
  
3.  選取可用性群組，然後展開 **[可用性複本]** 節點。  
  
4.  此步驟取決於您要移除多個複本或只要移除一個複本，如下所示：  
  
    -   若要移除多個複本，請使用 **[物件總管詳細資料]** 窗格檢視及選取您要移除的所有複本。 如需詳細資訊，請參閱[使用物件總管詳細資料監視可用性群組 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-object-explorer-details-to-monitor-availability-groups.md)。  
  
    -   若要移除單一複本，請在 **[物件總管]** 窗格或 **[物件總管詳細資料]** 窗格中選取它。  
  
5.  以滑鼠右鍵按一下選取的一或多個次要複本，然後在命令功能表中選取 [從可用性群組移除]。  
  
6.  在 **[從可用性群組移除次要複本]** 對話方塊中，若要移除所有列出的次要複本，按一下 **[確定]**。 如果您不要移除所有列出的複本，請按一下 **[取消]**。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **若要移除次要複本**  
  
1.  連接到裝載主要複本的伺服器執行個體。  
  
2.  使用 [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) 陳述式，如下所示：  
  
     ALTER AVAILABILITY GROUP *group_name* REMOVE REPLICA ON '*instance_name*' [,...*n*]  
  
     其中 *group_name* 是可用性群組的名稱，而 *instance_name* 是次要複本所在的伺服器執行個體。  
  
     下列範例會將次要複本從 *MyAG* 可用性群組中移除。 目標次要複本位於名為 *COMPUTER02* 之電腦上的 *HADR_INSTANCE*具名伺服器執行個體上。  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG REMOVE REPLICA ON 'COMPUTER02\HADR_INSTANCE';  
    ```  
  
##  <a name="PowerShellProcedure"></a> 使用 PowerShell  
 **若要移除次要複本**  
  
1.  將目錄 (**cd**) 變更為裝載主要複本的伺服器執行個體。  
  
2.  使用 **Remove-SqlAvailabilityReplica** Cmdlet。  
  
     例如，下列命令會將伺服器上的 `MyReplica` 可用性複本從名為 `MyAg`的可用性群組中移除。  此命令必須在裝載可用性群組之主要複本的伺服器執行個體上執行。  
  
    ```  
    Remove-SqlAvailabilityReplica `   
    -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  若要檢視 Cmdlet 的語法，請在 **PowerShell 環境中使用** Get-Help [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Cmdlet。 如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)。  
  
 **若要設定和使用 SQL Server PowerShell 提供者**  
  
-   [SQL Server PowerShell 提供者](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
##  <a name="PostBestPractices"></a> 追蹤：移除次要複本之後  
 如果您指定目前無法使用的複本，當複本連線時，將會發現該複本已經遭到移除。  
  
 移除複本會使它停止接收資料。 當次要複本確認它已從全域存放區移除之後，複本會從其資料庫移除可用性群組設定，處於 RECOVERING 狀態時，這些設定仍然存在於本機伺服器執行個體上。  
  
## <a name="see-also"></a>另請參閱  
 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [將次要複本新增至可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)   
 [移除可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md)  
  
  
