---
title: "STSymDifference (geography 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STSymDifference (geography Data Type)
- STSymDifference_TSQL
dev_langs: TSQL
helpviewer_keywords: STSymDifference (geography Data Type)
ms.assetid: 82bbfa2c-a61b-4f41-9bf8-6f720f363bae
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c591f665b6f441face6a83aa9421fc47c5b0982
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="stsymdifference-geography-data-type"></a>STSymDifference (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回物件，表示所有點都會在某個**geography**執行個體或另一個**geography**執行個體，但不是在這兩個執行個體內的點。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STSymDifference ( other_geography )  
```  
  
## <a name="arguments"></a>引數  
 *other_geography*  
 這是另一個**geography**除了所在 STSymDistance() 所叫用的執行個體的執行個體。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別：**地理位置**  
  
 CLR 傳回類型： **SqlGeography**  
  
## <a name="remarks"></a>備註  
 如果這個方法永遠傳回 null 的空間參考識別碼 (Srid) **geography**例項不相符。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援大於半球的空間執行個體。 在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，伺服器上的可能結果集已擴充到**FullGlobe**執行個體。  
  
 只有當輸入執行個體包含圓弧線段時，結果才能包含圓弧線段。  
  
## <a name="examples"></a>範例  
  
### <a name="a-computing-the-symmetric-difference-of-two-polygons"></a>A. 計算兩個多邊形的對稱差異  
 下列範例使用 `STSymDifference()` 來計算兩個 `Polygon` 執行個體之間的對稱差異。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('POLYGON((-122.351 47.656, -122.341 47.656, -122.341 47.661, -122.351 47.661, -122.351 47.656))', 4326);  
SELECT @g.STSymDifference(@h).ToString();  
```  
  
### <a name="b-computing-the-symmetric-difference-with-fullglobe"></a>B. 計算與 FullGlobe 的對稱差異  
 下列範例會計算 `Polygon` 與 `FullGlobe` 之間的對稱差異。  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STSymDifference('FULLGLOBE').ToString();
 ```  
  
## <a name="see-also"></a>請參閱＜  
 [地理例項上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
