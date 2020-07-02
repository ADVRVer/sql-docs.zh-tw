---
title: sys.databases column_store_dictionaries （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_dictionaries_TSQL
- column_store_dictionaries
- column_store_dictionaries_TSQL
- sys.column_store_dictionaries
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_dictionaries catalog view
ms.assetid: 56efd563-2f72-4caf-94e3-8a182385c173
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e7ccd7c93d42cb30eeb2fc24b79c358d519579b6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764769"
---
# <a name="syscolumn_store_dictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  包含各資料列，分別代表 xVelocity 記憶體最佳化資料行存放區索引所使用的每一部字典。 字典是用於編碼部分的資料類型而非全部，因此資料行存放區索引中並非所有資料行都有字典。 字典存在的形式可能是主要字典 (適用所有區段)，且或許另有其他次要字典用於資料行各區段的特定子集。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**hobt_id**|**bigint**|具有此資料行存放區索引之資料表的堆積或 B 型樹狀目錄索引（HoBT）識別碼。|  
|**column_id**|**int**|從1開始的資料行存放區資料行識別碼。 第一個資料行的 ID = 1，第二個數據行的識別碼 = 2，依此類推。|  
|**dictionary_id**|**int**|有兩種與資料行區段相關聯的字典： global 和 local。 Dictionary_id 為0，表示在該資料行的所有資料行區段（每個資料列群組各一個）之間共用的全域字典。|  
|**version**|**int**|字典格式的版本。|  
|**type**|**int**|字典類型：<br /><br /> 1-包含**int**值的雜湊字典<br /><br /> 2-未使用<br /><br /> 3-包含字串值的雜湊字典<br /><br /> 4-包含**浮點**值的雜湊字典<br /><br /> 如需有關字典的詳細資訊，請參閱資料行存放區[索引指南](~/relational-databases/indexes/columnstore-indexes-overview.md)。|  
|**last_id**|**int**|字典中的最後一個資料識別碼。|  
|**entry_count**|**bigint**|字典中的項目數。|  
|**on_disk_size**|**bigint**|字典的大小 (以位元組為單位)。|  
|**partition_id**|**bigint**|指出資料分割識別碼。 在資料庫中，這是唯一的。|  
  
## <a name="permissions"></a>權限  
必須具備資料表的`VIEW DEFINITION`權限。 除非使用者也具有許可權，否則下列資料行會傳回 null `SELECT` ： last_id、entry_count data_ptr。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的物件目錄檢視](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [&#40;Transact-sql&#41;的目錄檢視](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄常見問題](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [all_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [computed_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [資料行存放區索引指南](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [資料行存放區索引指南](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

