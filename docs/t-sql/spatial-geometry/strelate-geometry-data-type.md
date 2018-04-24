---
title: STRelate (geometry 資料類型) | Microsoft Docs
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
- STRelate (geometry Data Type)
- STRelate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRelate (geometry Data Type)
ms.assetid: 9dcb5f58-35ab-4bb3-86ee-2d29eefba6d3
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8693f605615e289ca716b13d0f3ed8d7e6fb8a1e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="strelate-geometry-data-type"></a>STRelate (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  如果 **geometry** 執行個體與另一個 **geometry** 執行個體有關 (關聯性是由 Dimensionally Extended 9 Intersection Model (DE-9IM) 模式矩陣值所定義)，便傳回 1；否則會傳回 0。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STRelate ( other_geometry, intersection_pattern_matrix )  
```  
  
## <a name="arguments"></a>引數  
 *other_geometry*  
 這是要與進行 `STRelate()` 叫用的執行個體做比較的另一個 **geometry** 執行個體。  
  
 *intersection_pattern_matrix*  
 這是兩個 **geometry** 執行個體之間 DE-9IM 模式矩陣裝置的 **nchar(9)** 類型編碼可接受值字串。  
  
## <a name="remarks"></a>Remarks  
 如果 **geometry** 執行個體的空間參考識別碼 (SRID) 不相符，這個方法一律會傳回 Null。 如果矩陣的格式不正確，這個方法將會擲回 **ArgumentException**。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**bit**  
  
 CLR 傳回類型：**SqlBoolean**  
  
## <a name="examples"></a>範例  
 下列範例會使用 `STRelate()`，利用明確的 DE-9IM 模式測試兩個 **geometry** 執行個體是否在空間上不相鄰。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(5 5)', 0);  
SELECT @g.STRelate(@h, 'FF*FF****');  
```  
  
## <a name="see-also"></a>另請參閱  
 [幾何例項上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
