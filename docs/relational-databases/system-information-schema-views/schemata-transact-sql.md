---
title: "結構描述 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCHEMATA_TSQL
- SCHEMATA
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
- SCHEMATA view
ms.assetid: 69617642-0f54-4b25-b62f-5f39c8909601
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ac71e5f401f0eb411f7356d8bc4c15fa0a57c901
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="schemata-transact-sql"></a>SCHEMATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  針對目前資料庫中每個結構描述，各傳回一個資料列。 若要從這些檢視中擷取資訊，請指定完整的名稱**INFORMATION_SCHEMA。***view_name*。 若要擷取執行個體中的所有資料庫的相關資訊[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，查詢[sys.databases &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)目錄檢視。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**CATALOG_NAME**|**sysname**|目前資料庫的名稱|  
|**SCHEMA_NAME**|**nvarchar (**128**)**|傳回結構描述的名稱。|  
|**SCHEMA_OWNER**|**nvarchar (**128**)**|結構描述擁有者名稱。<br /><br /> **\*\*重要\* \*** 請勿使用 INFORMATION_SCHEMA 檢視來判斷物件的結構描述。 尋找物件之結構描述的唯一可靠方式就是查詢 sys.objects 目錄檢視。|  
|**DEFAULT_CHARACTER_SET_CATALOG**|**varchar (**6**)**|一律傳回 NULL。|  
|**DEFAULT_CHARACTER_SET_SCHEMA**|**varchar (**3**)**|一律傳回 NULL。|  
|**DEFAULT_CHARACTER_SET_NAME**|**sysname**|傳回預設字元集的名稱。|  

**範例**  
下列範例中，會傳回 master 資料庫中的結構描述的相關資訊：  
```sql  
SELECT * FROM master.INFORMATION_SCHEMA.SCHEMATA;
```  

## <a name="see-also"></a>請參閱＜  
 [系統檢視 &#40;TRANSACT-SQL &#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [資訊結構描述檢視 &#40;TRANSACT-SQL &#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.schemas &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.syscharsets &#40;TRANSACT-SQL &#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)  
  
  
