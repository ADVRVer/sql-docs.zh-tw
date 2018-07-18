---
title: sys.pdw_health_component_status_mappings (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4b2d572b79c15c369e33190c183c249de3b8fb0c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33179954"
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  定義之間的對應[!INCLUDE[ssDW](../../includes/ssdw-md.md)]元件狀態，而且製造商定義的元件名稱。  
  
|資料行名稱|資料類型|Description|範圍|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|屬性的唯一識別碼。<br /><br /> 屬性識別碼、 component_id，與 physical_name 形成這個檢視的索引鍵。|NOT NULL|  
|component_id|**int**|元件的識別碼。 請參閱[sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)。<br /><br /> 屬性識別碼、 component_id，與 physical_name 形成這個檢視的索引鍵。|NOT NULL|  
|physical_name|**nvarchar(32)**|製造商所定義的屬性名稱。<br /><br /> 屬性識別碼、 component_id，與 physical_name 形成這個檢視的索引鍵。|NOT NULL|  
|logical_name|**nvarchar(255)**|所定義的屬性名稱[!INCLUDE[ssDW](../../includes/ssdw-md.md)]。|NOT NULL<br /><br /> 0-裝置執行個體是唯一的。<br /><br /> 1-裝置執行個體不是唯一的。|  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲目錄檢視](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
