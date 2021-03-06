---
title: 指定中斷點篩選條件
description: 了解如何實作中斷點篩選條件，以限制只能在指定的電腦、作業系統處理序和執行緒上進行偵錯時，中斷點才會運作。
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 307e262c57409725014a202b4a48143b5228763e
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036297"
---
# <a name="specify-a-breakpoint-filter"></a>指定中斷點篩選條件

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

中斷點篩選條件會限制中斷點只能在指定的電腦、作業系統處理序和執行緒上運作。 中斷點篩選條件通常是在偵錯平行應用程式時使用。

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]
  
##  <a name="filter-considerations"></a><a name="BKMK_ActionConsiderations"></a> 篩選考量

中斷點篩選條件通常不會搭配 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具使用，因為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼和預存程序不是平行應用程式。  
  
#### <a name="to-specify-a-breakpoint-filter"></a>若要指定中斷點篩選條件  
  
1.  在編輯器視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [篩選]。  
  
     -或-  
  
     在 [中斷點] 視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [篩選]。  
  
2.  在 [中斷點篩選條件]**** 對話方塊中，使用 [篩選]**** 方塊來指定電腦 (依名稱) 或作業系統處理序和執行緒 (依名稱或識別碼)：  
  
    -   **MachineName** 是執行 Database Engine 執行個體的電腦。  
  
    -   **ProcessID**和 **ProcessName** 是執行 Database Engine 執行個體的作業系統處理序。  
  
    -   **ThreadID** 和 **ThreadName** 是在 Database Engine 執行個體中執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次、程序或函數的作業系統執行緒。  
  
3.  按一下 **[確定]** 實作變更，或按一下 **[取消]** 結束而不套用變更。  
  
## <a name="see-also"></a>另請參閱  
 [指定中斷點條件](./specify-a-breakpoint-condition.md)   
 [指定叫用計數](./specify-a-hit-count.md)   
 [指定中斷點動作](./specify-a-breakpoint-action.md)