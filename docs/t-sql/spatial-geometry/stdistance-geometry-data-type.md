---
title: "STDistance (geometry 資料型別) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance (geometry Data Type)
ms.assetid: ac815bc7-5342-4cc4-af40-c80a1c4c8b68
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4e6219da2655b6e190905166e6d650754381ae43
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="stdistance-geometry-data-type"></a>STDistance (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回 **geometry** 執行個體中的點與另一個 **geometry** 執行個體中的點之間的最短距離。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STDistance ( other_geometry )  
```  
  
## <a name="arguments"></a>引數  
 *other_geometry*  
 這是另一個**geometry** 執行個體，用來測量它與叫用 `STDistance()` 所在之執行個體之間的距離。 如果 *other_geometry* 是空的集合，`STDistance()` 會傳回 Null。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**float**  
  
 CLR 傳回類型：**SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 如果 **geometry** 執行個體的空間參考識別碼 (SRID) 不相符，`STDistance()` 一定會傳回 Null。  
  
## <a name="examples"></a>範例  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POINT(10 10)', 0);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>另請參閱  
 [空間索引概觀](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [幾何例項上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
