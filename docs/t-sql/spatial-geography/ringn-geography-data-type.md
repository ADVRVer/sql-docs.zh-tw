---
title: RingN (geography 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- RingN
- RingN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RingN method
ms.assetid: 30f47275-2727-4d22-bbec-c0c54bcb3ac2
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f310b91d1b08256f5da1809bbe8c0f3f478f9bce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ringn-geography-data-type"></a>RingN (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回 **geography** 執行個體的指定環形：`1 ≤ n ≤ NumRings()`。  
  
## <a name="syntax"></a>語法  
  
```  
  
.RingN (expression )  
```  
  
## <a name="arguments"></a>引數  
 *expression*  
 這是介於 1 和 **polygon** 執行個體中環形數之間的 **int** 運算式。  
  
## <a name="return-value"></a>傳回值  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geography**  
  
 CLR 傳回類型：**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 如果環形索引 **n** 的值小於 1，則這個方法會擲回 **ArgumentOutOfRangeException**。 環形索引值必須大於或等於 1，而且應該要小於或等於 `NumRings()` 傳回的數字。  
  
## <a name="examples"></a>範例  
 這個範例會建立具有兩個環形的 `Polygon` 例項，並傳回第二個環形。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.RingN(2).ToString();  
```  
  
## <a name="see-also"></a>另請參閱  
 [地理執行個體上擴充的方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [NumRings &#40;geography 資料類型&#41;](../../t-sql/spatial-geography/numrings-geography-data-type.md)  
  
  
