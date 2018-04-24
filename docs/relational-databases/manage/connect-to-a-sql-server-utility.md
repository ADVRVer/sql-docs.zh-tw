---
title: 連接至 SQL Server 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2406fb1df47ec2005980c331942fee9bac106a0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="connect-to-a-sql-server-utility"></a>連接至 SQL Server 公用程式
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  在您可以連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式之前，您必須建立公用程式控制點 (UCP)。 如需詳細資訊，請參閱 [SQL Server 公用程式的功能與工作](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)。  
  
 若要檢視及管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源健全狀況，請使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式。  
  
 若要透過 SSMS 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式：  
  
1.  啟動 SSMS。  
  
2.  在 SSMS 中，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。  
  
3.  按一下 [檢視]，然後按一下 [公用程式總管]。  
  
4.  在公用程式總管瀏覽窗格中，按一下 [連接到公用程式] ![](../../relational-databases/manage/media/connect-to-utility.gif "Connect_to_Utility")。  
  
5.  在 [連接到伺服器] 對話方塊中，指定 UCP 執行個體名稱，然後按一下 [連接]。  
  
6.  檢視公用程式總管導覽窗格，以查看 UCP 中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源的樹狀檢視。  
  
 建立新的 UCP 也會連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式。 如需詳細資訊，請參閱[建立 SQL Server 公用程式控制點 &#40;SQL Server 公用程式&#41;](../../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 公用程式的功能與工作](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [檢視資源健全狀況原則結果 &#40;SQL Server 公用程式&#41;](../../relational-databases/manage/view-resource-health-policy-results-sql-server-utility.md)  
  
  
