---
title: syspolicy_conditions (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_conditions
- syspolicy_conditions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_conditions view
ms.assetid: af97d26c-4bd5-4b08-be51-8419e3b2832c
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 09d52d9a4c4d5005a51057a40c29524301d3fdd4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="syspolicyconditions-transact-sql"></a>syspolicy_conditions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中，針對每一個以原則為基礎的管理條件各顯示一個資料列。 syspolicy_conditions 屬於 msdb 資料庫內的 dbo 結構描述。 下表描述 syspolicy_conditions 檢視表中的資料行。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|condition_id|**int**|此條件的識別碼。 每一個條件都代表一或多個條件運算式的集合。|  
|name|**sysname**|此條件的名稱。|  
|date_created|**datetime**|建立此條件的日期和時間。|  
|description|**nvarchar(max)**|此條件的描述 描述資料行為選擇性，而且可為 NULL。|  
|created_by|**sysname**|建立此條件的登入。|  
|modified_by|**sysname**|最近修改此條件的登入。 如果從未修改過，則為 NULL。|  
|date_modified|**datetime**|建立此條件的日期和時間。 如果從未修改過，則為 NULL。|  
|is_name_condition|**smallint**|指定條件是否為命名條件。<br /><br /> 0 = 條件運算式不包含 @Name 變數。<br /><br /> 1 = 條件運算式包含 @@Name 變數。|  
|facet|**nvarchar(max)**|此條件所根據之 Facet 的名稱。|  
|運算式|**nvarchar(max)**|Facet 狀態的運算式。|  
|obj_name|**sysname**|如果條件運算式包含 @Name 變數，則為指派給此變數的物件名稱。|  
  
## <a name="remarks"></a>備註  
 當您針對以原則為基礎的管理進行疑難排解時，請查詢 syspolicy_conditions 檢視表來判斷建立此條件或上次變更此條件的人。  
  
## <a name="permissions"></a>Permissions  
 需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來管理伺服器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [以原則為基礎的管理檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
