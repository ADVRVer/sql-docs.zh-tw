---
title: MSSQLSERVER_8642 | Microsoft Docs
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
- 8642 (Database Engine error)
ms.assetid: fc498059-202f-4d0b-8599-4e784b47c186
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 33be055df4424a65830a90e68770c63c03c1f0fd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver8642"></a>MSSQLSERVER_8642
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|8642|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|EXCHNGSTART_ERR|  
|訊息文字|查詢處理器無法為平行查詢的執行啟動必要的執行緒資源。|  
  
## <a name="explanation"></a>說明  
伺服器中的執行緒資源不足。  
  
## <a name="user-action"></a>使用者動作  
減少伺服器的負載，然後重新執行查詢。  
  
