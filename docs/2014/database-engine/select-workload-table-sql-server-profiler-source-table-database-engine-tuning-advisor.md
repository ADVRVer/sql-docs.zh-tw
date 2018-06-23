---
title: SQL Server Profiler-來源資料表 Database Engine Tuning Advisor-選取工作負載資料表 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8b5ccfddb032fb3833e517632290cfdf7d82e643
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36029869"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a>SQL Server Profiler-來源資料表 Database Engine Tuning Advisor-選取工作負載資料表
  Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 和 [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor 使用此對話方塊來選取資料表。  
  
 在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 中，使用 [來源資料表] 對話方塊以指定追蹤資料表的來源資料表。 此資料表是追蹤載入的來源，並且可以檢視或使用其內容來重新執行追蹤。  
  
 在 [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor 中，使用 [選取工作負載資料表] 對話方塊，來選取包含 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 追蹤資訊的資料庫資料表用來作為微調工作負載，或在啟動微調分析之前預覽資料表內容。  
  
## <a name="options"></a>選項。  
 **[SQL Server]**  
 指定目前連接之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體。 此欄位會自動擴展且無法更新。  
  
 **[資料庫備份]**  
 指定追蹤資料表所在的資料庫。  
  
 **[擁有者]**  
 指定追蹤資料表的擁有者。 此欄位會自動擴展為 **dbo**。  
  
 **Table**  
 指定從中讀取追蹤的追蹤資料表名稱。  
  
## <a name="see-also"></a>另請參閱  
 [將追蹤結果儲存至資料表&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)   
 [SQL Server Profiler 範本和權限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Database Engine Tuning Advisor](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  