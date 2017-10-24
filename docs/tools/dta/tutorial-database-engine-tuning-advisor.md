---
title: "教學課程： Database Engine Tuning Advisor |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], tutorials
- tutorials [Database Engine Tuning Advisor]
ms.assetid: 3b54cbbe-d8c6-424d-92f1-aa58179f4da8
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8ca6d555b129e216dcff7f2ba6793aa844d3a4b8
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="tutorial-database-engine-tuning-advisor"></a>教學課程：Database Engine Tuning Advisor
歡迎使用 Database Engine Tuning Advisor 教學課程。 Database Engine Tuning Advisor 會檢查在您指定的資料庫中如何處理查詢，之後，它會建議您如何修改資料庫結構 (如索引、索引檢視和資料分割) 來改進查詢處理效能。  
  
Database Engine Tuning Advisor 提供兩個使用者介面：圖形化使用者介面 (GUI) 和 **dta** 命令提示字元公用程式。 GUI 可讓您既快又容易檢視微調工作階段的結果， **dta** 公用程式則可以輕易將 Database Engine Tuning Advisor 功能納入自動微調的指令碼中。 此外，Database Engine Tuning Advisor 可接受 XML 輸入，對微調處理序提供更多控制權。  
  
## <a name="what-you-will-learn"></a>學習內容  
這個教學課程將告訴您如何導覽 Database Engine Tuning Advisor GUI，以及如何利用這個 GUI 和 **dta** 公用程式來執行某些基本工作。 它包含下列課程：  
  
[Database Engine Tuning Advisor 中的第 1 課： 基本導覽](../../tools/dta/lesson-1-basic-navigation-in-database-engine-tuning-advisor.md)  
在這個課程中，您將熟悉新的 Database Engine Tuning Advisor GUI，以及學習如何設定顯示選項和配置。  
  
[第 2 課： 使用 Database Engine Tuning Advisor](../../tools/dta/lesson-2-using-database-engine-tuning-advisor.md)  
在這個課程中，您將學會如何使用 Database Engine Tuning Advisor GUI 來執行基本微調工作。  
  
[第 3 課： 使用 dta 命令提示字元公用程式](../../tools/dta/lesson-3-using-the-dta-command-prompt-utility.md)  
在這個課程中，您將學習如何啟動 **DTA** 命令提示字元公用程式，以及如何執行簡單的微調命令。  
  
## <a name="requirements"></a>需求  
這個教學課程是專門針對不熟悉 Database Engine Tuning Advisor GUI 或 **dta** 命令提示字元公用程式，但是熟悉資料庫概念和結構 (例如索引和索引檢視) 的資料庫管理員而提供。  
  
您必須安裝具有 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 範例資料庫的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] (或更新版本)。 為了加強安全性，依預設，不會安裝範例資料庫。 若要安裝範例資料庫，請參閱＜ [安裝 SQL Server 範例和範例資料庫](http://sqlserversamples.codeplex.com)＞。  
  
## <a name="after-you-finish-this-tutorial"></a>完成這個教學課程之後  
完成這個教學課程中的課程之後，請參閱下列主題，以取得有關 Database Engine Tuning Advisor 的詳細資訊：  
  
-   ＜[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) ＞提供如何利用這個工具來執行工作的描述。  
  
-   ＜[dta Utility](../../tools/dta/dta-utility.md) ＞提供有關命令提示字元公用程式的參考資料，以及可用來控制公用程式作業的選擇性 XML 檔案。  
  
## <a name="next-lesson"></a>下一課  
[Database Engine Tuning Advisor 中的第 1 課： 基本導覽](../../tools/dta/lesson-1-basic-navigation-in-database-engine-tuning-advisor.md)  
  
  
  

