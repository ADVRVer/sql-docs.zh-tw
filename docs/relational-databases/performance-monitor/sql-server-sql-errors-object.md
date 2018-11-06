---
title: SQL Server 的 SQL Errors 物件 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 15639c63e44e5c81c7b7d7bc4302ef8bd883db22
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033495"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server 的 SQL Errors 物件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Microsoft **中的** SQLServer:SQL Errors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件，提供用來監視 **SQL Errors**的計數器。  
  
 下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** 計數器。  
  
|SQL Server SQL Errors 計數器|Description|  
|------------------------------------|-----------------|  
|**Errors/sec**|每秒的錯誤數目。|  
  
 物件中的每個計數器均包含下列執行個體：  
  
|項目|定義|  
|----------|----------------|  
|**_Total**|所有錯誤的相關資訊。|  
|**DB Offline Errors**|追蹤導致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 讓目前資料庫離線的嚴重錯誤。|  
|**Info Errors**|針對僅提供資訊給使用者而不會導致錯誤的錯誤訊息，提供其相關資訊。|  
|**Kill Connection Errors**|追蹤導致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 清除目前連接的嚴重錯誤。|  
|**User Errors**|使用者錯誤的相關資訊。|  
  
## <a name="see-also"></a>另請參閱  
 [監視資源使用狀況 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
