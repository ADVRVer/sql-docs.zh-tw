---
title: sys.masked_columns (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 432ea847081c8f0060954efdd6e7f2beea1a592d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33179294"
---
# <a name="sysmaskedcolumns-transact-sql"></a>sys.masked_columns (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  使用**sys.masked_columns**檢視來查詢的資料表的資料行具有動態資料遮罩套用至這些函式。 此檢視繼承自 **sys.columns** 檢視。 它會傳回 **sys.columns** 檢視中的所有資料行，加上 **is_masked** 和 **masking_function** 資料行，指出資料行是否已遮罩，若已遮罩，則指出定義了哪個遮罩函數。 此檢視只會顯示已套用遮罩函數的資料行。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|這個資料行所屬的物件識別碼。|  
|name|**sysname**|資料行的名稱。 在物件中，這是唯一的。|  
|column_id|**int**|資料行的識別碼。 在物件中，這是唯一的。<br /><br /> 資料行識別碼不一定會循序排列。|  
|**sys.masked_columns**傳回許多更多的資料行繼承自**sys.columns**。|各種|請參閱[sys.columns &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)的多個資料行定義。|  
|is_masked|**bit**|指出資料行加上遮罩。 1 表示遮罩。|  
|masking_function|**nvarchar(4000)**|資料行的遮罩函數。|  
  
## <a name="remarks"></a>備註  
  
## <a name="permissions"></a>Permissions  
 在使用者具有資料表上的某種權限，或如果使用者有 VIEW ANY DEFINITION 權限，此檢視會傳回資料表的相關資訊。  
  
## <a name="example"></a>範例  
 下列查詢會聯結**sys.masked_columns**至**sys.tables**傳回有關所有遮罩資料行。  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>另請參閱  
 [動態資料遮罩](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
