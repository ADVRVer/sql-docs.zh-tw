---
title: "STNumPoints (geometry 資料類型) |Microsoft 文件"
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
- STNumPoints_TSQL
- STNumPoints (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STNumPoints (geometry Data Type)
ms.assetid: a19520fc-7f91-4a2c-856f-4d8b99a7e496
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17dc20837c72439fc79fec62170edfb8eca34d9a
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="stnumpoints-geometry-data-type"></a>STNumPoints (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  在每一個圖形內傳回的點數總和**幾何**執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STNumPoints ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別： **int**  
  
 CLR 傳回類型： **SqlInt32**  
  
## <a name="remarks"></a>備註  
 這個方法會計算的描述中的點**幾何**執行個體。 重複的點都會被算入。 如果這個執行個體**集合**型別，這個方法會傳回的點數總和中每個項目。  
  
## <a name="examples"></a>範例  
 下列範例會建立 `LineString` 例項，並使用 `STNumPoints()` 來判斷例項描述內所用的點數。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STNumPoints();  
```  
  
## <a name="see-also"></a>另請參閱  
 [幾何例項上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

