---
title: STSymDifference (geometry 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STSymDifference_TSQL
- STSymDifference (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STSymDifference (geometry Data Type)
ms.assetid: 1d4cf35a-ca89-4aa4-ae30-e61a0ff18b53
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 36322b4046264f80094914a6db1fb1c1ce421a31
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="stsymdifference-geometry-data-type"></a>STSymDifference (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  傳回物件，表示在某個 **geometry** 執行個體或另一個 **geometry** 執行個體內的所有點 (但不是同時在這兩個執行個體內的點)。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STSymDifference ( other_geometry )  
```  
  
## <a name="arguments"></a>引數  
 *other_geometry*  
 這是除了 `STSymDistance()` 叫用所在的執行個體之外的另一個 **geometry** 執行個體。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geometry**  
  
 CLR 傳回類型：**SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 如果 **geometry** 執行個體的空間參考識別碼 (SRID) 不相符，這個方法一律會傳回 Null。 只有當輸入執行個體包含圓弧線段時，結果才能包含圓弧線段。  
  
## <a name="examples"></a>範例  
  
### <a name="a-computing-the-symmetric-difference-of-two-polygon-instances"></a>A. 計算兩個 Polygon 執行個體的對稱差異  
 下列範例使用 `STSymDifference()` 來計算兩個 `Polygon` 執行個體之間的對稱差異。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STSymDifference(@h).ToString();  
```  
  
### <a name="b-computing-the-symmetric-difference-between-a-curvepolygon-and-a-polygon-instance"></a>B. 計算 CurvePolygon 和 Polygon 執行個體之間的對稱差異  
 下列範例會傳回 `GeometryCollection`，代表 `CurvePolygon` 與 `Polygon` 之間的對稱差異。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 SELECT @h.STSymDifference(@g).ToString();
 ```  
  
## <a name="c-using-stsymdifference-on-curvepolygon-instance-with-an-inscribed-polygon-instance"></a>C. 在具有內切 Polygon 執行個體的 CurvePolygon 執行個體上使用 STSymDifference()  
 下列範例會傳回具有 `CurvePolygon` 內環的 `Polygon` 執行個體，代表兩個相比較執行個體之間的對稱差異。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 2 -1, 2 1, 1 1, 1 -1))';  
 SELECT @h.STSymDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>另請參閱  
 [幾何例項上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
