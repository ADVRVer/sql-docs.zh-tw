---
title: STOverlaps (geometry 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STOverlaps (geometry Data Type)
- STOverlaps_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STOverlaps (geometry Data Type)
ms.assetid: 1813cba1-5780-456a-9489-6b40a79569b3
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 392b39ae14819aa645e4714189f17e6d4604bf44
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "68140920"
---
# <a name="stoverlaps-geometry-data-type"></a>STOverlaps (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

如果 **geometry** 執行個體與另一個 **geometry** 執行個體重疊，便傳回 1。 如果不是則傳回 0。
  
## <a name="syntax"></a>語法  
  
```  
  
.STOverlaps ( other_geometry )  
```  
  
## <a name="arguments"></a>引數  
 *other_geometry*  
 這是要與叫用 **所在之執行個體相比較的另一個**geometry`STOverlaps()` 執行個體。  
  
## <a name="return-types"></a>傳回型別  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**bit**  
  
 CLR 傳回類型：**SqlBoolean**  
  
## <a name="remarks"></a>備註  
 兩個 **geometry** 執行個體重疊的條件是：代表其交集的區域與這兩個執行個體的維度相同，而且區域不等於任一個執行個體。  
  
 如果 `STOverlaps()`geometry **執行個體相交的點不是相同的維度，** 一律會傳回 0。  
  
 如果 **geometry** 執行個體的空間參考識別碼 (SRID) 不相符，這個方法一律會傳回 Null。  
  
## <a name="examples"></a>範例  
 下列範例會使用 `STOverlaps()` 來測試兩個 **geometry** 執行個體是否重疊。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STOverlaps(@h);  
```  
  
## <a name="see-also"></a>另請參閱  
 [幾何例項上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

