---
title: "sys.table_types (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- table_types_TSQL
- sys.table_types
- sys.table_types_TSQL
- table_types
dev_langs:
- TSQL
helpviewer_keywords:
- table types [SQL Server]
- table-valued parameters, sys.table_types
- sys.table_types
- UDTT
ms.assetid: c05fd873-aff2-4a89-9936-a54c2ea09996
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9c55e83d67fcd5817575b0b045bb680b0269217
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systabletypes-transact-sql"></a>sys.table_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用者定義資料表類型的屬性。 資料表類型是指可以從中宣告資料表變數或資料表值參數的類型。 每個資料表類型都具有**type_table_object_id**也就是外部索引鍵到[sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)目錄檢視。 您可以使用此識別碼資料行來查詢各種目錄檢視，類似的方式**object_id**規則資料表，以探索資料表類型，例如其資料行和條件約束的結構資料行。    
 
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|*\<繼承資料行 >*||如需這個檢視所繼承的資料行的清單，請參閱[sys.types &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md).|  
|**type_table_object_id**|**int**|物件識別碼。 此碼在資料庫中是唯一的。|  
|**is_memory_optimized**|**bit**|**適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 以下是可能的值：<br /><br /> 0 = 不是記憶體最佳化的<br /><br /> 1 = 是記憶體最佳化的<br /><br /> 預設值是 0 值。<br /><br /> 資料表類型一定會使用 DURABILITY = SCHEMA_ONLY 來建立。 只有結構描述會在磁碟上保存。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [物件目錄檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [使用資料表值參數 &#40; Database Engine &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
