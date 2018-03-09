---
title: "篩選事件，依據事件開始時間 (SQL Server Profiler) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cfd8b7593b4e43613483a6ce91cf279ade6b91bc
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>依據事件開始時間篩選事件 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]本主題描述如何篩選追蹤事件使用，根據事件開始時間[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]。  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>若要依據事件開始時間篩選事件  
  
1.  在 [檔案] 功能表上按一下 [新增追蹤]，然後連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。  
  
     會出現 [追蹤屬性] **[追蹤屬性]**對話方塊。  
  
    > [!NOTE]  
    >  如果選取 [進行連接後立即啟動追蹤]，將不會顯示 [追蹤屬性] 對話方塊，而是開始追蹤。 在 [工具] 功能表上，按一下 [選項]，並清除 [進行連接後立即啟動追蹤] 核取方塊，以關閉這項設定。  
  
2.  在 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。  
  
3.  在 [使用範本] 名稱清單中，選取追蹤範本。  
  
4.  選擇性地指定追蹤結果的目的地。  
  
5.  在 [事件選取範圍] 索引標籤上，按一下 [開始時間] 資料行標題。 您也可以用滑鼠右鍵按一下資料行標題，然後按一下 [編輯資料行篩選] 以啟動 [編輯篩選] 對話方塊。  
  
6.  展開 [大於] 或 [小於]，然後在比較運算子下出現的欄位中輸入 <日期時間> 值。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
