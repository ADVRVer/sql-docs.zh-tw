---
title: Database 事件類別目錄 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0d725f95fc8e9de0865ad895abd860d5f03687b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "62662926"
---
# <a name="database-event-category"></a>Database 事件類別目錄
  **Database** 事件類別目錄包含用來監視 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的事件類別。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[Data File Auto Grow 事件類別](data-file-auto-grow-event-class.md)|表示資料檔案自動成長。 如果以外顯方式透過 ALTER DATABASE 讓資料檔案成長，則不會觸發這個事件。|  
|[Data File Auto Shrink 事件類別](data-file-auto-shrink-event-class.md)|指出資料檔案已壓縮。|  
|[Database Mirroring Connection 事件類別](database-mirroring-connection-event-class.md)|為報告資料庫鏡像的傳輸連接狀態而產生的事件。|  
|[Database Mirroring State Change 事件類別](database-mirroring-state-change-event-class.md)|指出鏡像資料庫的狀態何時變更。|  
|[Database Suspect Data Page 事件類別](database-suspect-data-page-event-class.md)|指出頁面何時加入至 **msdb** 資料庫中的 **suspect_pages** 資料表。|  
|[Log File Auto Grow 事件類別](log-file-auto-grow-event-class.md)|表示記錄檔自動成長。 如果以外顯方式透過 ALTER DATABASE 讓記錄檔增長，則不會觸發這個事件。|  
|[Log File Auto Shrink 事件類別](log-file-auto-shrink-event-class.md)|表示記錄檔自動成長。 如果透過 ALTER DATABASE 來明確壓縮記錄檔，則不會觸發此事件。|  
  
## <a name="see-also"></a>另請參閱  
 [擴充事件](../extended-events/extended-events.md)  
  
  
