---
title: "在 SQL Server 容錯移轉叢集中裝載報表伺服器資料庫 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
caps.latest.revision: "5"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 8ee0e2234fbc9f4da7a333be6da318eade46760c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>在 SQL Server 容錯移轉叢集中裝載報表伺服器資料庫
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供容錯移轉叢集支援，可讓您針對一或多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體使用多個磁碟。 只有報表伺服器資料庫才支援容錯移轉叢集。您無法將報表伺服器服務當做容錯移轉叢集的一部分執行。  
  
 若要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集上主控報表伺服器資料庫，必須已經安裝及設定該叢集。 然後，在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具的 [資料庫安裝] 頁面中建立報表伺服器資料庫時，您就可以選取容錯移轉叢集當做伺服器名稱。  
  
 雖然報表伺服器服務無法參與容錯移轉叢集，但是您可以在已安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 容錯移轉叢集的電腦上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 報表伺服器的執行與容錯移轉叢集無關。 如果您在屬於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉執行個體之一部分的電腦上安裝報表伺服器，就不需要針對報表伺服器資料庫使用容錯移轉叢集。您可以使用不同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體來主控此資料庫。  
  
## <a name="see-also"></a>另請參閱  
 [報表伺服器資料庫 &#40;SSRS 原生模式&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [建立報表伺服器資料庫 &#40;SSRS 組態管理員&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)  
  
  
