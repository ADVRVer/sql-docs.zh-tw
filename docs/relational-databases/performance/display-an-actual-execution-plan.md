---
title: 顯示實際執行計畫 | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: performance
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 01e8796ec210078d2ae45896e269063a35f4142b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="display-an-actual-execution-plan"></a>顯示實際執行計畫
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]產生實際的圖形執行計畫。 實際執行計畫是在執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢或 Batch 後產生。 因為這個緣故，實際執行計畫會包含執行階段資訊，如實際資源使用計量和執行階段警告等 (如果有的話)。 所產生的執行計畫會顯示 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行查詢所使用的實際查詢執行計畫。  
  
 若要使用這個功能，使用者必須具有適當權限，以便執行將會產生圖形執行計畫的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢，同時也需將查詢所參考之所有資料庫的 SHOWPLAN 權限，都授與給使用者。  
  
### <a name="to-include-an-execution-plan-for-a-query-during-execution"></a>若要在執行期間包括查詢的執行計畫  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 工具列上，按一下 [Database Engine 查詢]。 您也可以按一下 [開啟檔案] 工具列按鈕並找出現有的查詢，以開啟現有的查詢並顯示估計執行計畫。 
  
2.  輸入您希望顯示其實際執行計畫的查詢。  
  
3.  在 [查詢] 功能表上，按一下 [包括實際執行計畫] 或按一下 [包括實際執行計畫] 工具列按鈕  
  
4.  按一下 [執行] 工具列按鈕執行查詢。 查詢最佳化工具所使用的計畫，會顯示在結果窗格的 [執行計畫] 索引標籤上。 將滑鼠游標暫時放在邏輯與實體運算子上，即可在顯示的 [工具提示] 中檢視運算子的說明與屬性。  
  
     或者，您可以在 [屬性] 視窗中檢視運算子屬性。 如果沒有看到 [屬性] 視窗，請以滑鼠右鍵按一下運算子，然後選取 [屬性]。 選取運算子以檢視其屬性。  
  
5.  您可以用滑鼠右鍵按一下執行計畫，然後選取 [放大]、[縮小]、[自訂顯示比例] 或 [縮放至適當比例]，來改變執行計畫的顯示。 [放大] 及 [縮小] 可讓您放大或縮小執行計畫，而 [自訂顯示比例] 則可讓您定義自己的顯示比例，如 80% 的顯示比例。 [縮放至適當比例] 會放大執行計畫，以符合結果窗格的大小。 或者，使用 CTRL 鍵加滑鼠滾輪，啟動**動態縮放**。  
  
 
 > [!NOTE] 
 > 或者，使用 [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)，在執行各陳述式後傳回其執行計畫資訊。 如果用於 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，[結果] 索引標籤會有連結，以圖形格式開啟執行計畫。   
