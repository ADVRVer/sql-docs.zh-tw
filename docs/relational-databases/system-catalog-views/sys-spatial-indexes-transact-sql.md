---
title: sys.databases spatial_indexes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.spatial_indexes_TSQL
- spatial_indexes
- spatial_indexes_TSQL
- sys.spatial_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_indexes catalog view
ms.assetid: 40e967d5-2e8d-45af-bf5e-5251493cf7cb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7aa52b0f559ecae832d0236d534d9752b86a3d20
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883756"
---
# <a name="sysspatial_indexes-transact-sql"></a>sys.spatial_indexes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  表示空間索引的主要索引資訊。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|\<inherited columns>||從[sys.databases](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)繼承資料行。|  
|spatial_index_type|**tinyint**|空間索引的類型：<br /><br /> 1 = 幾何空間索引<br /><br /> 2 = 地理空間索引|  
|spatial_index_type_desc|**nvarchar(60)**|輸入空間索引的描述：<br /><br /> GEOMETRY = 幾何空間索引<br /><br /> GEOGRAPHY = 地理空間索引|  
|tessellation_scheme|**sysname**|鑲嵌式配置的名稱：<br /><br /> GEOMETRY_GRID、GEOMETRY_AUTO_GRID、<br /><br /> GEOGRAPHY_GRID、GEOGRAPHY_AUTO_GRID<br /><br /> 注意：如需鑲嵌式配置的詳細資訊，請參閱[空間索引總覽](../../relational-databases/spatial/spatial-indexes-overview.md)。|  
|\<inherited columns>||從[sys.databases](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)繼承資料行。<br /><br /> 繼承的資料行 has_filter 和 filter_definition 會出現在空間索引特有的資料行後面。|  
  
## <a name="permissions"></a>權限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [spatial_index_tessellations &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-spatial-index-tessellations-transact-sql.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [index_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [空間索引概觀](../../relational-databases/spatial/spatial-indexes-overview.md)  
  
  
