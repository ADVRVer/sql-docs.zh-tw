---
title: MSSQLSERVER_8966 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bb2f83db75535b7960d110a17ef6bbc26dc7f968
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8966"></a>MSSQLSERVER_8966
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|8966|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBCC3_FAILED_TO_READ_AND_LATCH_PAGE|  
|訊息文字|無法使用閂鎖類型 TYPE 來讀取和閂鎖頁面 P_ID。 作業失敗。|  
  
## <a name="explanation"></a>說明  
頁面讀取失敗或無法針對 PFS 或 GAM 頁面採用閂鎖。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中可能有閂鎖逾時或其他隨附的訊息。  
  
## <a name="user-action"></a>使用者動作  
請檢閱 SQL 錯誤記錄檔，以便找出隨附的訊息並解決這些錯誤。  
  
