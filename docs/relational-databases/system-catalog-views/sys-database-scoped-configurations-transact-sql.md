---
title: sys.database_scoped_configurations (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
caps.latest.revision: 13
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 373d2933d362f565799518bfe1af516ad1943276
ms.sourcegitcommit: 0cc2cb281e467a13a76174e0d9afbdcf4ccddc29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172987"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  包含每個組態的一個資料列。 
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|組態選項的識別碼。|  
|**name**|**nvarchar(60)**|組態選項的名稱。 如需可能的設定資訊，請參閱[ALTER DATABASE SCOPED CONFIGURATION &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)。|  
|**value**|**sqlvariant**|此為主要複本的組態選項所設定的值。|  
|**value_for_secondary**|**sqlvariant**|設定次要複本的此組態選項的值。|  
|**elevate_online**|**nvarchar(60)** |資料庫範圍的索引作業將 online 選項的預設集 |
|**elevate_resumable**|nvarchar(60)|資料庫範圍索引作業的繼續選項預設的集| 
  
##  <a name="Permissions"></a> Permissions  
 需要 **public** 角色中的成員資格。  
  
## <a name="remarks"></a>備註  
 當傳回做為值的 NULL **value_for_secondary**，這表示次要資料庫會設定為主要。  
 
 資料庫範圍組態設定會伴隨著資料庫。 這意謂著還原或附加指定的資料庫時，現有的組態設定會持續存留。
  
## <a name="see-also"></a>另請參閱  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
