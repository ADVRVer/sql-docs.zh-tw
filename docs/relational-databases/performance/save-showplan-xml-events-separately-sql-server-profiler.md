---
title: "個別儲存 Showplan XML 事件 (SQL Server Profiler) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: 33320a7a-36e8-401c-876d-5b82c49abd85
caps.latest.revision: "25"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 106a627a50964d482776401bf27db6f2c83ac0ea
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2018
---
# <a name="save-showplan-xml-events-separately-sql-server-profiler"></a>個別儲存 Showplan XML 事件 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 本主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，將在追蹤中擷取的 **Showplan XML** 事件儲存到個別的 .SQLPlan 檔案中。 您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中開啟 **Showplan XML** 事件檔案，以便檢視每個事件的圖形化執行計畫。  
  
## <a name="save-showplan-xml-events-separately"></a>個別儲存 Showplan XML 事件  
  
1. 在 [檔案] 功能表上選取 [新增追蹤]，然後連線到 SQL Server 的執行個體。  
  
     會出現 [追蹤屬性]  對話方塊。  
  
    > [!NOTE]  
    >  如果選取 [進行連線後立即啟動追蹤]，將不會顯示 [追蹤屬性] 對話方塊，而是開始追蹤。 若要關閉這個設定，請在 [工具] 功能表上選取 [選項]，然後清除 [進行連線後立即啟動追蹤] 核取方塊。  
  
2. 在 **[追蹤屬性]** 對話方塊的 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。  
  
3. 在 [使用範本] 清單中，選取追蹤使用為基礎的追蹤範本。 若不想要使用範本，請選取 [空白]。  
  
4. 執行下列其中之一：  
  
    -   若要將追蹤擷取至檔案，請選取 [儲存至檔案] 核取方塊。 在 **[設定最大檔案大小]**中指定一個值。 
    
        (選擇性) 選取 **[啟用檔案換用]** 與 **[伺服器處理追蹤資料]** 核取方塊。  
  
    -   若要將追蹤擷取至資料庫資料表，請選取 [儲存至資料表] 核取方塊。 
    
        (選擇性) 選取 [設定最大資料列數]，然後指定一個值。  
  
5. (選擇性) 選取 **[啟用追蹤停止時間]** 核取方塊，然後指定停止日期和時間。 
  
6. 選取 [事件選取範圍] 索引標籤。  
  
7. 在 [事件] 資料行中，展開 [Performance] 事件類別目錄，然後選取 [Showplan XML] 核取方塊。 如果看不到 [Performance] 事件類別目錄，請選取 [顯示所有事件] 來顯示它。  
  
     [事件擷取設定] 索引標籤會新增至 [追蹤屬性] 對話方塊。  
  
8. 在 [事件擷取設定] 索引標籤上，選取 [個別儲存 XML 執行程序表事件]。  
  
9. 在 **[另存新檔]** 對話方塊中，輸入儲存 **Showplan XML** 事件的檔案名稱。  
  
10. 選取 [所有 XML 執行程序表批次都在單一檔案中]，以便將所有 **Showplan XML** 事件儲存到單一 XML 檔案中。 或者選取 [每一個 XML 執行程序表批次都在相異檔案中]，針對每個 **Showplan XML** 事件建立新的 XML 檔案。  
  
11. 若要在 SQL Server Management Studio 中檢視 **Showplan XML** 事件，請在 [檔案] 功能表上指向 [開啟]，然後選取 [檔案]。 瀏覽至您儲存一或多個 **Showplan XML** 事件檔案的目錄，以便選取一個檔案並加以開啟。 **Showplan XML** 事件檔案的副檔名為 .SQLPlan。  
  
## <a name="see-also"></a>另請參閱  
 [在 SQL Server Profiler 中使用執行程序表結果分析查詢](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
