---
title: "sys.trace_categories (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- trace_categories
- trace_categories_TSQL
- sys.trace_categories
- sys.trace_categories_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.trace_categories catalog view
ms.assetid: f6a86766-e2a9-4d9f-a073-1b59e888ba7d
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5c686db19c3c9136cbd50e83b34a7b542721df95
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="systracecategories-transact-sql"></a>sys.trace_categories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  依類別目錄來分組類似的事件類別。 每個資料列**sys.trace_categories**目錄檢視識別類別目錄伺服器中是唯一的。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 給定版本的這些類別目錄不會改變。  
  
 如需支援的追蹤事件完整清單，請參閱[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)。  
  
> **重要！** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]請改用擴充事件目錄檢視。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**smallint**|這個類別目錄的唯一識別碼。 此資料行也是**sys.trace_events**目錄檢視。|  
|**name**|**nvarchar （128)**|這個類別目錄的唯一名稱。 這個參數未翻譯成當地語系。|  
|**型別**|**tinyint**|類別目錄類型：<br /><br /> 0 = 正常<br /><br /> 1 = 連接<br /><br /> 2 = 錯誤|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [物件目錄檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.traces &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys.trace_columns &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys.trace_events &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys.trace_event_bindings &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys.trace_subclass_values &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
