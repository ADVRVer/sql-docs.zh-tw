---
title: MSSQLSERVER_5237 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d7d9dc07600323fe8621a480201a8dab673ce4f6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver5237"></a>MSSQLSERVER_5237
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|5237|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|訊息文字|物件 'NAME' (物件識別碼 O_ID) 的 DBCC 跨資料列集檢查失敗，因為發生內部查詢錯誤。|  
  
## <a name="explanation"></a>說明  
由於發生內部錯誤，導致 DBCC 無法執行查詢來檢查索引檢視表。  
  
## <a name="user-action"></a>使用者動作  
重新執行 DBCC 命令。  
  
