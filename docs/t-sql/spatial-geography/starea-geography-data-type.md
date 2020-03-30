---
title: STArea (geography 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 817a6325b956f5fc4214597b0b8bc46f6aff49f3
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "68042516"
---
# <a name="starea-geography-data-type"></a>STArea (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回 **geography** 執行個體的總介面區。 STArea () 的結果，是**地理**執行個體的空間參考識別碼所使用測量平方單位。 例如，如果執行個體的 SRID 是4326，則 STArea () 會以平方公尺傳回結果。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>傳回型別  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**float**  
  
CLR 傳回類型：**SqlDouble**  
  
## <a name="remarks"></a>備註  
如果 **geography** 執行個體僅包含 0 維度和 1 維度的圖形 (或為空白)，則 STArea() 會傳回 0。  
  
> [!NOTE]  
>  產生度量傳回值之 **geography** 資料類型上的方法將會根據此方法中使用之執行個體的 SRID 而有不同的結果。 如需有關 SRID 的詳細資訊，請參閱[空間參考識別碼 &#40;SRIDs&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)。  
  
## <a name="examples"></a>範例  
下列範例會使用 `STArea()` 建立 `Polygon geography` 執行個體，並計算此多邊形的區域。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>另請參閱  
[地理例項上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
