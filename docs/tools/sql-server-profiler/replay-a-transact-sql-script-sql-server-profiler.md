---
title: "重新執行 TRANSACT-SQL 指令碼 (SQL Server Profiler) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b9de32b90da72311b4d239d9b734bd97f8b60c5
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2017
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>重新執行 Transact-SQL 指令碼 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]當測試效能問題的可能方案時，使用[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]重新執行[!INCLUDE[tsql](../../includes/tsql-md.md)]指令碼，並比較變更前後的效能。  
  
### <a name="to-replay-a-transact-sql-script"></a>若要重新執行 Transact-SQL 指令碼  
  
1.  在 [檔案] 功能表上，指向 [開啟]，然後按一下 [指令碼檔案]。  
  
2.  選取您要開啟的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼檔案。 確定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼包含重新執行所需的事件。 如需詳細資訊，請參閱 [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md)。  
  
3.  在 [重新執行] 功能表上，按一下 [啟動]，然後連接到您要重新執行指令碼的伺服器。  
  
4.  在 **[重新執行組態]** 對話方塊中確認設定，然後按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [重新執行追蹤](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
