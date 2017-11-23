---
title: "sys.dm_fts_population_ranges (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_population_ranges
- sys.dm_fts_population_ranges_TSQL
- dm_fts_population_ranges_TSQL
- dm_fts_population_ranges
dev_langs: TSQL
helpviewer_keywords: sys.dm_fts_population_ranges dynamic management view
ms.assetid: 58d8564b-9c43-4965-a31c-2893890334ef
caps.latest.revision: "31"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 06ca4f5bc4232621bcc027696f1f778633f1942c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmftspopulationranges-transact-sql"></a>sys.dm_fts_population_ranges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回與目前正在進行的全文檢索索引擴展相關之特定範圍的資訊。  
   
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**memory_address**|**varbinary （8)**|針對與這個全文檢索索引母體擴展子範圍有關之活動所配置的記憶體緩衝區位址。|  
|**parent_memory_address**|**varbinary （8)**|代表與全文檢索索引相關之母體擴展所有範圍的父物件記憶體緩衝區位址。|  
|**is_retry**|**bit**|如果其值為 1，這個子範圍就負責重試發生錯誤的資料列。|  
|**session_id**|**smallint**|目前正在處理這項工作的工作階段識別碼。|  
|**processed_row_count**|**int**|這個範圍已處理的資料列數。 向前進度會進行保存，而且每 5 分鐘計算一次，而不是每批次認可計算一次。|  
|**error_count**|**int**|這個範圍已發生錯誤的資料列數。 向前進度會進行保存，而且每 5 分鐘計算一次，而不是每批次認可計算一次。|  
  
## <a name="permissions"></a>Permissions  
在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]Premium 層需要`VIEW DATABASE STATE`資料庫的權限。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]標準和基本層，需要**伺服器管理員**或**Azure Active Directory 系統管理員**帳戶。  

## <a name="physical-joins"></a>實體聯結  
 ![這個動態管理檢視的重要聯結](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-population-ranges-1.gif "此動態管理檢視的重要聯結")  
  
## <a name="relationship-cardinalities"></a>關聯性基數  
  
|來源|若要|關聯性|  
|----------|--------|------------------|  
|dm_fts_population_ranges.parent_memory_address|dm_fts_index_population.memory_address|多對一|  
  
## <a name="see-also"></a>請參閱＜  
  [全文檢索搜尋及語意搜尋動態管理檢視與函數 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

