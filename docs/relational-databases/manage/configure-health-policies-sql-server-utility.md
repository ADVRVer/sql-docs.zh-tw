---
title: 設定健康狀態原則 (SQL Server 公用程式) | Microsoft Docs
description: 了解如何設定涉及 SQL Server 的資料層應用程式和受控執行個體的處理器使用率及檔案空間的健康情況原則。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 75b2f80a8f2d8aeed3bb5858c8de7dd07ef1419c
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91868692"
---
# <a name="configure-health-policies-sql-server-utility"></a>設定健康情況原則 (SQL Server 公用程式)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 公用程式儀表板，針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 受管理的執行個體和資料層應用程式檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式資源參數。 如需詳細資訊，請參閱 [SQL Server 公用程式的功能與工作](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)。  
  
 若要檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式健全狀況原則結果，請從 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]連接到公用程式控制點。 如需詳細資訊，請參閱 [使用公用程式總管來管理 SQL Server 公用程式](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以針對資料層應用程式和受管理的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體來設定公用程式健全狀況原則。 您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內針對所有資料層應用程式和受管理的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體來以全域方式定義健全狀況原則，或者可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內針對每一個資料層應用程式及每一個受管理的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體來個別定義健全狀況原則。  
  
## <a name="monitoring-policies-for-data-tier-applications"></a>監視資料層應用程式的原則  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料層應用程式的使用量過高和使用量過低原則如下：  
  
-   資料層應用程式的處理器使用率。  
  
-   適用於資料庫檔案的資料層應用程式檔案空間。  
  
-   適用於存放磁碟區的資料層應用程式檔案空間。  
  
-   電腦處理器使用率。  
  
> [!NOTE]  
>  對於資料層應用程式而言，存放磁碟區和處理器使用率是唯讀原則。  
  
 如需有關檢視或變更資料層應用程式之全域監視原則的詳細資訊，請參閱[公用程式管理 &#40;SQL Server 公用程式&#41;](/previous-versions/sql/sql-server-2016/ee240832(v=sql.130))。  
  
 如需有關檢視或變更個別資料層應用程式監視原則的詳細資訊，請參閱[部署的資料層應用程式詳細資料 &#40;SQL Server 公用程式&#41;](/previous-versions/sql/sql-server-2016/ee240857(v=sql.130))。  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a>SQL Server Managed 執行個體的監視原則  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Managed 執行個體的使用量過高和使用量過低原則如下：  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體處理器使用率。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體檔案空間。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體檔案空間。  
  
-   電腦處理器使用率。  
  
 如需有關檢視或變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 受管理的執行個體之全域監視原則的詳細資訊，請參閱[公用程式管理 &#40;SQL Server 公用程式&#41;](/previous-versions/sql/sql-server-2016/ee240832(v=sql.130))。  
  
 如需有關檢視或變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 個別受管理的執行個體之監視原則的詳細資訊，請參閱[受管理的執行個體詳細資料 &#40;SQL Server 公用程式&#41;](./utility-explorer-f1-help.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 公用程式的功能與工作](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [降低 CPU 使用量原則的雜訊 &#40;SQL Server 公用程式&#41;](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
