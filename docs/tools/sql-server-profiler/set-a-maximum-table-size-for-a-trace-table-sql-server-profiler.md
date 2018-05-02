---
title: 設定追蹤資料表的資料表大小上限 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e286bd012ca83e2505ec3ab742836e586380f10
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MTE
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>設定追蹤資料表的資料表大小上限 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本主題說明如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來設定追蹤資料表的資料表大小上限。  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>若要設定追蹤資料表的大小上限  
  
1.  在 **[檔案]** 功能表上按一下 **[新增追蹤]**，然後連接到 SQL Server 的執行個體。  
  
     會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。  
  
    > [!NOTE]  
    >  如果選取 [進行連接後立即啟動追蹤]，將不會顯示 [追蹤屬性] 對話方塊，而是開始追蹤。 於 [工具] 功能表，按一下 [選項]，並清除 [連接後立即啟動追蹤] 核取方塊，以關閉這項設定。  
  
2.  在 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。  
  
3.  在 [範本名稱] 清單中，選取追蹤範本。  
  
4.  選取 [儲存至資料表] 核取方塊。  
  
5.  連接到您要儲存追蹤的伺服器。  
  
     畫面上出現 [目的地資料表] 對話方塊。  
  
6.  從 [資料庫] 清單中選取追蹤的資料庫。  
  
7.  在 [資料表] 方塊中，輸入或選取資料表名稱。  
  
8.  選取 [設定最大資料列數] 核取方塊，並指定追蹤資料表的最大資料列數。  
  
    > [!NOTE]  
    >  當資料表的資料列數超過您所指定的最大值時，就不會再記錄追蹤事件。 不過，仍會繼續追蹤。  
  
## <a name="see-also"></a>另請參閱  
 [[SQL Server Profiler]](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
