---
title: MSSQLSERVER_17128 | Microsoft Docs
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
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 49d7bcd7b89ddc8fa170b17be500c988b993502b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|17128|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|INIT_NOBUFSPACE|  
|訊息文字|initdata: 未提供記憶體給核心緩衝區。|  
  
## <a name="explanation"></a>說明  
緩衝集區的初始記憶體配置或保留已經失敗，而且 SQL Server 結束。  
  
## <a name="user-action"></a>使用者動作  
通常是由於在非常小型的電腦 (遠低於最低系統需求) 上啟動 SQL Server 所造成。  
  
