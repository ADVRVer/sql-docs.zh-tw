---
title: "STLength (geography 資料類型) |Microsoft 文件"
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
- STLength (geography Data Type)
- STLength_TSQL
dev_langs: TSQL
helpviewer_keywords: STLength method
ms.assetid: 774560ab-4a4a-4058-b043-1e67cf6fb9eb
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a1b261b3774fdd093185be5cab70561c6f32a11b
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="stlength-geography-data-type"></a>STLength (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  傳回的項目中的總長度**geography**執行個體或**geography**內**GeometryCollection**。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別： **float**  
  
 CLR 傳回類型： **SqlDouble**  
  
## <a name="remarks"></a>備註  
 如果**geography**執行個體關閉後，其長度會計算為此例項周圍的總長度; 任何多邊形的長度是它的周長，而且點的長度為 0。 長度**GeometryCollection**的計算所有的長度總和**geography**包含在集合內的執行個體。  
  
 STLength() 可在有效與無效的 LineString 上運作。 一般而言，LineString 無效的原因是重疊的線段，而這可能是由不正確的 GPS 追蹤等異常所造成。 STLength() 不會移除重疊或無效的線段。 它會在所傳回的長度值中包含重疊和無效的線段。 MakeValid() 方法可以從 LineString 中移除重疊的線段。  
  
## <a name="examples"></a>範例  
 下列範例會建立 `LineString` 執行個體，並使用 `STLength()` 來尋找此執行個體的長度。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>另請參閱  
 [地理例項上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
