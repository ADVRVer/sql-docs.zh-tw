---
title: "STDimension (geography 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDimension (geography Data Type)
- STDimension_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STDimension method
ms.assetid: 4368b0f6-0678-4ade-87dc-b43d8b2e8d92
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0026ae44feb99e398a4502488d52594dac3b6bd4
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="stdimension-geography-data-type"></a>STDimension (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回的最大維度**geography**執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別： **int**  
  
 CLR 傳回類型： **SqlInt32**  
  
## <a name="remarks"></a>備註  
 STDimension() 傳回-1，如果**geography**是空的執行個體。  
  
## <a name="examples"></a>範例  
 下列範例會使用`STDimension()`建立資料表變數來保存`geography`例項，並插入`Point`、 `LineString`，和`Polygon`。  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geography);  
  
INSERT INTO @temp values ('Point', geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326));  
INSERT INTO @temp values ('LineString', geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
INSERT INTO @temp values ('Polygon', geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 然後，範例會傳回每個維度`geography`執行個體。  
  
|name|dim|  
|----------|---------|  
|點|0|  
|LineString|1|  
|多邊形|2|  
  
## <a name="see-also"></a>另請參閱  
 [Geography 執行個體上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

