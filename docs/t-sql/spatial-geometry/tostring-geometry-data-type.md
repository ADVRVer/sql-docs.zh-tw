---
title: "ToString (geometry 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ToString (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 06bf05558bfefdf679d479429f5e71afcfcb7c6b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="tostring-geometry-data-type"></a>ToString (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回開放式地理空間協會 (Open Geospatial Consortium，OGC) 對於幾何例項的已知的文字 (Well-Known Text，WKT) 表示法，經由此例項夾帶的任何 Z (高度) 和 M (測量) 值來擴充。
  
## <a name="syntax"></a>語法  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別： **nvarchar （max)**  
  
 CLR 傳回類型： **SqlString**  
  
## <a name="remarks"></a>備註  
 這個方法在 Null 例項上呼叫時，將會傳回 "Null" 字串。  
  
 在非 Null 例項上，此方法相當於使用 `AsTextZM().`  
  
## <a name="examples"></a>範例  
 下列範例會建立`LineString`執行個體，並使用`ToString()`擷取執行個體的文字描述。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>請參閱＜  
 [STAsText &#40; geometry 資料類型 &#41;](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)   
 [幾何例項上擴充的方法](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

