---
title: STGeomCollFromText (geometry 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeomCollFromText_TSQL
- STGeomCollFromText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromText (geometry Data Type)
ms.assetid: 19e757b3-cb2e-4852-87b9-40a815ab707e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7b4398107b11ff0bb1764dc70e4af24af082aeb4
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "68107709"
---
# <a name="stgeomcollfromtext-geometry-data-type"></a>STGeomCollFromText (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

從開放地理空間協會 (Open Geospatial Consortium，OGC) 的已知的文字 (Well-Known Text，WKT) 表示法傳回 **geometry** 執行個體，經由此執行個體夾帶的任何 Z (高度) 和 M (測量) 值來擴充。
  
## <a name="syntax"></a>語法  
  
```  
  
STGeomCollFromText ( 'geometrycollection_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>引數  
 *geometrycollection_tagged_text*  
 這是要傳回之 **geometry** 執行個體的 WKT 表示法。 *geometry_tagged_text* 是一個 **nvarchar(max)** 運算式。  
  
 *SRID*  
 這是 **int** 運算式，代表要傳回之 **geometry** 執行個體的空間參考識別碼 (SRID)。  
  
## <a name="return-types"></a>傳回型別  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geometry**  
  
 CLR 傳回類型：**SqlGeometry**  
  
## <a name="remarks"></a>備註  
 **所傳回之**geometry`STGeomCollFromText()` 執行個體的 OGC 類型會設定為對應的 WKT 輸入。  
  
 如果輸入無效，這個方法將會擲回例外狀況。  
  
## <a name="examples"></a>範例  
 下列範例會使用 `STGeomCollFromText()` 建立幾何例項。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION ( POLYGON((5 5, 10 5, 10 10, 5 5)), POINT(10 10) )', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另請參閱  
 [OGC 靜態幾何方法](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

