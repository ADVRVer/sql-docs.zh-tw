---
title: SQL Server 的 Memory Broker Clerks 物件 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: 546d5052c2b97b40b4f7e979c0447c947fdf487a
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906028"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server, Memory Broker Clerks 物件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**SQLServer:Memory Broker Clerks** 效能物件提供與記憶體 Broker Clerk 相關之統計資料的計數器。

下表說明 SQL Server **Memory Broker Clerks** 效能物件。

|**SQL Server Memory Broker Clerks 計數器**|Description|  
|-------------|-----------------|  
|**Internal benefit**|項目計數壓力的記憶體內部值 (單位: 毫秒/每頁/每毫秒)，乘以 100 億並截斷為整數。|
|**Memory broker clerk size**|Clerk 的大小 (以頁為單位)。|
|**Periodic evictions (pages)**|上次定期收回時從 Broker Clerk 收回的頁面數目。|
|**Pressure evictions (pages/sec)**|記憶體不足時每秒從 Broker Clerk 收回的頁面數目。|
|**Simulation benefit**|至 Clerk 的記憶體值 (單位: 毫秒/每頁/每毫秒)，乘以 100 億並截斷為整數。|
|**Simulation size**|Clerk 模擬的目前大小 (以頁為單位)。|

緩衝集區和資料行存放區物件集區都有計數器的執行個體。

## <a name="see-also"></a>另請參閱  
[監視資源使用狀況 (系統監視器)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
