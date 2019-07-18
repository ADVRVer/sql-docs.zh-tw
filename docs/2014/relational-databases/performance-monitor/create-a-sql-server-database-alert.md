---
title: 建立 SQL Server 資料庫警示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7c95605ed1a0ab42340713c5c5fa635b09d4a8ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63249483"
---
# <a name="create-a-sql-server-database-alert"></a>建立 SQL Server 資料庫警示
  您可以使用「系統監視器」來建立警示，讓它在達到「系統監視器」計數器的臨界值時引發。 為了回應此警示，「系統監視器」可啟動某個應用程式，諸如撰寫來處理此警示條件的自訂應用程式。 例如，您可以建立一個警示，讓它在死結 (Deadlock) 個數超過特定數值時引發。  
  
 您也可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來定義警示。 如需詳細資訊，請參閱 [警示](../../ssms/agent/alerts.md)。  
  
 如需使用「系統監視器」來建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫警示的詳細資訊，請參閱[設定 SQL Server 資料庫警示 &#40;Windows&#41;](../performance/set-up-a-sql-server-database-alert-windows.md)。  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql)  
  
  
