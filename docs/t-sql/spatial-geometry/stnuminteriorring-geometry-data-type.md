---
title: "STNumInteriorRing (geometry 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STNumInteriorRing_TSQL
- STNumInteriorRing (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STNumInteriorRing (geometry Data Type)
ms.assetid: 48e78948-5b14-41dd-85d1-169bba1c4195
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c424d1804897062be3eefc6c8240c9973bb1d92d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="stnuminteriorring-geometry-data-type"></a>STNumInteriorRing (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回的內部環形數**Polygongeometry**執行個體。
  
## <a name="syntax"></a>語法  
  
```  
  
.STNumInteriorRing ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別： **int**  
  
 CLR 傳回類型： **SqlInt32**  
  
## <a name="remarks"></a>備註  
 如果此方法會傳回 null**幾何**執行個體不是多邊形。  
  
## <a name="examples"></a>範例  
 下列範例會建立 `Polygon` 例項，並使用 `STNumInteriorRing()` 來尋找此例項具有多少內環。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STNumInteriorRing();  
```  
  
## <a name="see-also"></a>另請參閱  
 [幾何例項上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


