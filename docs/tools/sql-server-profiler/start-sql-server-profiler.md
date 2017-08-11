---
title: "執行 SQL Server Profiler |Microsoft 文件"
ms.custom: 
ms.date: 7/7/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
- Profiler [SQL Server Profiler], running
- SQL Server Profiler, running
- running SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9ce18e13fa735921846ea7f564ff53983d0c2dca
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="run-sql-server-profiler"></a>執行 SQL Server Profiler
  您可以執行[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]數種不同方式，以支援收集追蹤輸出中的各種案例。 您可以啟動[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]從 Windows 10**啟動**功能表上，從**工具**功能表中的[!INCLUDE[ssDE](../../includes/ssde-md.md)]Tuning Advisor，並從數個位置中[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。  
  
當您第一次啟動[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]選取**新追蹤**從**檔案**功能表中，應用程式會顯示**連接到伺服器**對話方塊中，您可以在其中指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]来連接至執行個體。  
## <a name="to-start-sql-server-profiler-from-the-windows-10-start-menu"></a>若要從 Windows 10 的 [開始] 功能表啟動 SQL Server Profiler  
-  按一下 Windows**啟動**圖示或按 Windows 鍵，然後開始輸入 「 SQL Server Profiler 17"。 當**SQL Server Profiler 17**磚出現時，按一下它。   

## <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>在 Database Engine Tuning Advisor 中啟動 SQL Server Profiler  
-  在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor 的 **[工具]** 功能表上，按一下 **[SQL Server Profiler]**。  

## <a name="to-start-sql-server-profiler-in-sql-server-management-studio"></a>若要啟動 SQL Server Management Studio 中的 SQL Server Profiler  
 您可以啟動[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]從數個位置中[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。 當[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]啟動時，它會載入連接內容、 追蹤範本及其啟動點的篩選內容。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]在自己的執行個體中啟動每個 SQL Server Profiler 工作階段和程式碼剖析工具會繼續執行，如果您關閉[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。  
### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>從工具功能表啟動 SQL Server Profiler  
-  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tuning Advisor 中的** 功能表上，按一下 **[SQL Server Profiler]**。  

### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>從查詢編輯器啟動 SQL Server Profiler  
- 在查詢編輯器中按一下滑鼠右鍵，然後選取 [在 SQL Server Profiler 中追蹤查詢]。  

  > [!NOTE]  
  >  連接內容是編輯器連接、追蹤範本為 TSQL_SPs，而套用的篩選為 SPID = 查詢視窗 SPID。  
    
### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>若要從活動監視器啟動 SQL Server Profiler  
- 在 活動監視器 中，按一下 **處理程序** 窗格中，以滑鼠右鍵按一下您想要設定檔，然後按一下 處理序**在 SQL Server Profiler 中追蹤處理序**。  

    > [!NOTE]  
    >  選取處理序時，如果有開啟 [活動監視器]，則連接內容為 [物件總管] 連接。 追蹤範本是以伺服器類型為基礎的預設值，而且 SPID 等於所選處理序的 SPID。  
    
## <a name="net-framework-security"></a>.NET Framework 安全性  
- 在 Windows 驗證模式中，使用者帳戶執行[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]必須連接到的執行個體的權限[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
- 若要利用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來執行追蹤，使用者也必須有 ALTER TRACE 權限。  

## <a name="next-steps"></a>後續的步驟  
 [SQL Server Profiler 概觀](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [使用 SQL Server Management Studio](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  

