---
title: "STDimension (geometry 資料型別) | Microsoft Docs"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDimension_TSQL
- STDimension (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDimension (geometry Data Type)
ms.assetid: 4fbd27dd-317b-4916-a8ae-4df1b8a6f27c
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 76b9f0dfc0745dbef3713c2102b75ad280a3ff50
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="stdimension-geometry-data-type"></a>STDimension (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回 **geometry** 執行個體的最大維度。
  
## <a name="syntax"></a>語法  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**int**  
  
 CLR 傳回類型：**SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 如果 **geometry** 執行個體是空的，`STDimension()` 會傳回 -1。  
  
## <a name="examples"></a>範例  
 下列範例會建立資料表變數來保存 **geometry** 執行個體，並插入 `Point`、`LineString` 和 `Polygon`。  然後使用 `STDimension()` 傳回每一個 **geometry** 執行個體的維度。  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geometry);  
INSERT INTO @temp values ('Point', geometry::STGeomFromText('POINT(3 3)', 0));  
INSERT INTO @temp values ('LineString', geometry::STGeomFromText('LINESTRING(0 0, 3 3)', 0));  
INSERT INTO @temp values ('Polygon', geometry::STGeomFromText('POLYGON((0 0, 3 0, 0 3, 0 0))', 0));  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 然後此範例會傳回每一個 `geometry` 執行個體的維度。  
  
|NAME|dim|  
|----------|---------|  
|點|0|  
|LineString|@shouldalert|  
|多邊形|2|  
  
## <a name="see-also"></a>另請參閱  
 [幾何例項上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

