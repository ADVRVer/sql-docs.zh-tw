---
title: "STEquals (geography 資料類型) |Microsoft 文件"
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
- STEquals_TSQL
- STEquals (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STEquals method
ms.assetid: 0766ff37-0b9e-49bf-83c0-019f4354fe44
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43b86d121e1877f63465398ace833c84321c0096
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="stequals-geography-data-type"></a>STEquals (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  傳回 1，如果**geography**執行個體代表相同的點與另一個集合**geography**執行個體。 如果不是則傳回 0。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STEquals ( other_geography )  
```  
  
## <a name="arguments"></a>引數  
 *other_geography*  
 這是另一個**geography**比較所在之執行個體的執行個體`STEquals()`叫用。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別：**位元**  
  
 CLR 傳回類型： **SqlBoolean**  
  
## <a name="remarks"></a>備註  
 如果這個方法永遠傳回 null 的空間參考識別碼 (Srid) **geography**例項不相符。  
  
## <a name="examples"></a>範例  
 下列範例會建立兩個`geography`與執行個體`STGeomFromText()`會相等，但是並不完全相同，而且會使用`STEquals()`來測試是否相等。 這些例項相等，因為 `LINESTRING` 和 `POINT` 包含在 `POLYGON` 內。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('GEOMETRYCOLLECTION(POLYGON((-122.368 47.658, -122.338 47.649, -122.338 47.658, -122.368 47.658, -122.368 47.658)), LINESTRING(-122.360 47.656, -122.343 47.656), POINT (-122.35 47.656))', 4326);  
SET @h = geography::STGeomFromText('POLYGON((-122.368 47.658, -122.338 47.649, -122.338 47.658, -122.368 47.658, -122.368 47.658))', 4326);  
SELECT @g.STEquals(@h);  
```  
  
## <a name="see-also"></a>另請參閱  
 [地理例項上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
