---
title: "sys.key_constraints (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.key_constraints
- key_constraints
- sys.key_constraints_TSQL
- key_constraints_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.key_constraints catalog view
ms.assetid: 0f782d2f-7126-46ab-85b7-bcba44862231
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ade8a9ce0fc36b9f7dfe2f1b7d098d23f00e791
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="syskeyconstraints-transact-sql"></a>sys.key_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  針對每個本身是主索引鍵或唯一條件約束的物件，各包含一個資料列。 包含**sys.objects.type** PK 和 UQ。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**\<從 sys.objects 繼承的資料行 >**||如需這個檢視所繼承的資料行的清單，請參閱[sys.objects &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**unique_index_id**|**int**|在為了強制執行這個條件約束而建立的父物件中，對應的唯一索引鍵之識別碼。|  
|**is_system_named**|**bit**|1 = 名稱是系統所產生。<br /><br /> 0 = 名稱是使用者所提供。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [物件目錄檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄常見問題集](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
