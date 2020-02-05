---
title: STPointN (geography 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointN_TSQL
- STPointN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointN method
ms.assetid: 47670feb-b9e0-4b4b-af83-b9bba7da66ac
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 12ae393f99510df743b5a5ec0bf777f7b982d570
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "68120815"
---
# <a name="stpointn-geography-data-type"></a>STPointN (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回 **geography** 執行個體中的指定點。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>引數  
 *expression*  
 這是介於 1 和 **geography** 執行個體中點數間的 **int** 運算式。  
  
## <a name="return-types"></a>傳回型別  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geography**  
  
 CLR 傳回類型：**SqlGeography**  
  
 開放地理空間協會 (OGC) 類型：**Point**  
  
## <a name="remarks"></a>備註  
 如果 **geography** 執行個體是使用者建立的，STPointN() 會傳回 *expression* 所指定的點，其方式是根據原來輸入的順序來排序這些點。  
  
 如果 **geography** 執行個體是系統建構的，STPointN() 會傳回 *expression* 所指定的點，其方式是根據輸出的相同順序來排序所有點：首先是根據 **geography** 執行個體，然後是根據執行個體內的環形 (如果適用的話)，再根據環形內的點。 這個順序具決定性。  
  
 如果使用小於 1 的值來呼叫此方法，它會擲回 **ArgumentOutOfRangeException**。  
  
 如果使用大於例項中點數的值來呼叫此方法，它會傳回 Null。  
  
## <a name="examples"></a>範例  
 下列範例會建立 `LineString` 例項，並使用 `STPointN()` 來擷取例項描述中的第二個點。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a>另請參閱  
 [地理例項上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
