---
title: sys.dm_pdw_component_health_status (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 51e364650f8b8f8dae386126bdc820f9c72e571c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899514"
---
# <a name="sysdmpdwcomponenthealthstatus-transact-sql"></a>sys.dm_pdw_component_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  保留應用裝置元件的目前健全狀況的相關資訊。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||非 NULL|  
|component_id|ssNoversion|元件的識別碼。 請參閱[sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)。<br /><br /> pdw_node_id、 component_id、 屬性識別碼和 component_instance_id 形成此檢視的索引鍵。|非 NULL|  
|property_id|**int**|屬性的識別碼。 請參閱[sys.pdw_health_component_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md)。|NOT NULL|  
|component_instance_id|**nvarchar(255)**|識別元件的執行個體。 比方說，CPU 的執行個體可能會識別 component_instance_id = 'CPU1'。<br /><br /> pdw_node_id、 component_id、 屬性識別碼和 component_instance_id 形成此檢視的索引鍵。|NOT NULL|  
|property_value|**nvarchar(255)**|目前的屬性值。|NULL|  
|update_time|**datetime**|上次更新的計量。|NOT NULL|  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理檢視&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
