---
title: "sys.triggers (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- triggers
- triggers_TSQL
- sys.triggers
- sys.triggers_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.triggers catalog view
ms.assetid: cefa4fc4-b8b9-4cd7-b124-eed5283acbfc
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ab5788614af71fe9fa4cab1a4f22e81d5a19a6d8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systriggers-transact-sql"></a>sys.triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  針對每個 TR 或 TA 類型的觸發程序物件，各包含一個資料列。 DML 觸發程序名稱是由結構描述限定範圍，因此會顯示在**sys.objects**。 而 DDL 觸發程序名稱是由父實體來限定範圍，因此只會顯示在這份檢視中。  
  
 **Parent_class**和**名稱**唯一識別資料行在資料庫中的觸發程序。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|觸發程序名稱。 DML 觸發程序名稱是由結構描述限定範圍。 DDL 觸發程序名稱是以父實體來限定範圍。|  
|**object_id**|**int**|物件識別碼。 在資料庫中，這是唯一的。|  
|**parent_class**|**tinyint**|觸發程序父系的類別。<br /><br /> 0 = DDL 觸發程序的資料庫。<br /><br /> 1 = DML 觸發程序的物件或資料行。|  
|**parent_class_desc**|**nvarchar （60)**|觸發程序父類別的描述。<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**sys.internal_tables**|**int**|觸發程序父系的識別碼，如下所示：<br /><br /> 0 = 以資料庫為父系的觸發程序。<br /><br /> DML 觸發程序，這是**object_id**的資料表或檢視定義的 DML 觸發程序。|  
|**型別**|**char(2)**|物件類型：<br /><br /> TA = 組件 (CLR) 觸發程序<br /><br /> TR = SQL 觸發程序|  
|**type_desc**|**nvarchar （60)**|物件類型的描述。<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|建立觸發程序的日期。|  
|**modify_date**|**datetime**|上次利用 ALTER 陳述式來修改物件的日期。|  
|**is_ms_shipped**|**bit**|利用內部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件來代表使用者所建立的觸發程序。|  
|**sys.indexes**|**bit**|觸發程序已停用。|  
|**is_not_for_replication**|**bit**|觸發程序是建立為 NOT FOR REPLICATION。|  
|**is_instead_of_trigger**|**bit**|1 = INSTEAD OF 觸發程序<br /><br /> 0 = AFTER 觸發程序。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [安全性目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
