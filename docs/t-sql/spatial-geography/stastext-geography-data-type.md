---
title: "STAsText (geography 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
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
- STAsText (geography Data Type)
- STAsText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STAsText method
ms.assetid: d3d2635d-ca6c-4205-9d6c-eb939ee314fd
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c41abc14564547efa56be18cb1fa18bfa0443f2e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="stastext-geography-data-type"></a>STAsText (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回開放式地理空間協會 (OGC) 已知文字 (well-known text，WKT) 表示**geography**執行個體。 此文字將不會包含此執行個體所夾帶的任何 Z (高度) 或 M (測量) 值。  
  
 這**geography**資料類型方法可支援**FullGlobe**執行個體或大於半球的空間執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STAsText ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別： **nvarchar （max)**  
  
 CLR 傳回類型： **SqlChars**  
  
## <a name="remarks"></a>備註  
 OGC 類型**geography**執行個體由叫用[stgeometrytype （)](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md)。  
  
 在[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，傳回伺服器上的可能結果集已擴充到**FullGlobe**執行個體。  
  
## <a name="examples"></a>範例  
 下列範例會使用`STAsText()`建立`LineString``geography`的執行個體 （-122.360，47.656） 到 （-122.343，47.656） 的文字。 然後，它會在文字中傳回結果。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>另請參閱  
 [地理例項上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
