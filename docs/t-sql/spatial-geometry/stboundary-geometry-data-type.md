---
title: STBoundary (geometry 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STBoundary (geometry Data Type)
- STBoundary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBoundary (geometry Data Type)
ms.assetid: f0551674-e6e8-4926-9038-df03f2c807d7
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 671e27f0e35e450b89c3eaaadc3b31612114348a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65939090"
---
# <a name="stboundary-geometry-data-type"></a>STBoundary (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回 **geometry** 執行個體的界限。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STBoundary ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geometry**  
  
 CLR 傳回型別：**SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 當 **LineString**、**CircularString** 或 **CompoundCurve** 執行個體的端點相同時，`STBoundary()` 會傳回空的 **GeometryCollection**。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-stboundary-on-a-linestring-instance-with-different-endpoints"></a>A. 在具有不同端點的 LineString 執行個體上使用 STBoundary()  
 下列範例會建立 `LineString``geometry` 執行個體。 `STBoundary()` 會傳回 `LineString` 的界限。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STBoundary().ToString();  
```  
  
### <a name="b-using-stboundary-on-a-linestring-instance-with-the-same-endpoints"></a>B. 在具有相同端點的 LineString 執行個體上使用 STBoundary()  
 下列範例會建立具有相同端點的有效 `LineString` 執行個體。 `STBoundary()` 會傳回空的 `GeometryCollection`。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, -2 2, 0 0)', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
### <a name="c-using-stboundary-on-a-curvepolygon-instance"></a>C. 在 CurvePolygon 執行個體上使用 STBoundary()  
 下列範例會在 `STBoundary()` 執行個體上使用 `CurvePolygon`。 `STBoundary()` 會傳回 `CircularString` 執行個體。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(0 0, 2 2, 0 2, -2 2, 0 0))', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
## <a name="see-also"></a>另請參閱  
 [幾何例項上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
