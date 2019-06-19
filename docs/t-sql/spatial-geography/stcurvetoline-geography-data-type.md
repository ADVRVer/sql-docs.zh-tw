---
title: STCurveToLine (geography 資料型別) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCurveToLine_TSQL
- STCurveToLine
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveToLine method (geography)
ms.assetid: 2f863a85-6168-465a-b32f-bb5e3de58dee
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 7f237da350b47ea0c3141709cd82d083ef509196
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65939188"
---
# <a name="stcurvetoline-geography-data-type"></a>STCurveToLine (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回包含圓弧線段之 **geography** 執行個體的多邊形近似值。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STCurveToLine()  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geography**  
  
 CLR 傳回型別：**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 傳回 **CircularString** 或 **CompoundCurve** 執行個體的 **LineString** 執行個體。  
  
 傳回 **CurvePolygon** 執行個體的 **Polygon** 執行個體。  
  
 傳回 **geography** 執行個體的副本，其中不包含 **CircularString**、**CompoundCurve** 或 **CurvePolygon** 執行個體。  
  
 不同於 SQL MM 規格，這個方法不會使用計算多邊形近似值的 z 座標值。 呼叫 **geography** 執行個體中出現的任何 z 座標值都會被忽略。  
  
## <a name="examples"></a>範例  
 下列範例會傳回 `LineString` 執行個體，這是 `CircularString` 執行個體的多邊形近似值：  
  
```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography;  
 SET @g2 = @g1.STCurveToLine();  
 SELECT @g1.STNumPoints() AS G1, @g2.STNumPoints() AS G2;
 ```  
  
## <a name="see-also"></a>另請參閱  
 [STLength &#40;geography 資料型別&#41;](../../t-sql/spatial-geography/stlength-geography-data-type.md)   
 [STNumPoints &#40;geography 資料型別&#41;](../../t-sql/spatial-geography/stnumpoints-geography-data-type.md)   
 [空間資料類型概觀](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
