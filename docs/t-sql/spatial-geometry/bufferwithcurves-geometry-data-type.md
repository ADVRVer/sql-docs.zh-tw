---
title: "BufferWithCurves (geometry 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: BufferWithCurves method (geometry)
ms.assetid: 8ffaba3f-d2dd-4e57-9f41-3ced9f14b600
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2651ae4e2a4d245f61115438e959a6881ff1935f
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="bufferwithcurves-geometry-data-type"></a>BufferWithCurves (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  傳回**幾何**表示集合的所有執行個體從呼叫點距離**幾何**執行個體小於或等於*距離*參數。  
  
## <a name="syntax"></a>語法  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>引數  
 *distance*  
 是**float**點形成緩衝區的最大距離，表示可以從**幾何**執行個體。  
  
## <a name="return-types"></a>傳回類型  
SQL Server 傳回類型：**幾何**  
  
 CLR 傳回類型： **SqlGeometry**  
  
## <a name="exceptions"></a>例外狀況  
 下列準則會擲回**ArgumentException**。  
  
-   沒有參數傳遞至此方法，例如 `@g.BufferWithCurves()`  
  
-   非數值參數傳遞至此方法，例如 `@g.BufferWithCurves('a')`  
  
-   **NULL**傳遞至此方法，例如`@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>備註  
 下圖顯示由這個方法傳回的 geometry 執行個體範例。  
  
 ![BufferedCurve](../../t-sql/spatial-geometry/media/bufferedcurve.gif)
  
 下表顯示針對不同距離值所傳回的結果。  
  
|distance 值|維度類型|傳回的空間類型|  
|--------------------|---------------------|---------------------------|  
|distance < 0|零或一維|空白**GeometryCollection**執行個體|  
|distance < 0|二維或以上|A **CurvePolygon**或**GeometryCollection**具有負數緩衝的執行個體。 **注意：**負數緩衝可能會建立空**GeometryCollection**|  
|distance = 0|所有維度|叫用的複製**幾何**執行個體|  
|distance > 0|所有維度|**CurvePolygon**或**GeometryCollection**執行個體|  
  
> [!NOTE]  
>  因為*距離*是**float**，非常小的值可等同於零的計算中。 當發生這種情況再呼叫一份**幾何**會傳回執行個體。 請參閱[float 和 real &#40;TRANSACT-SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 負數緩衝會移除幾何界限之給定距離內的所有點。 下圖中，負數緩衝顯示為圓形淺色陰影區域。 點線是原始多邊形的界限，實線是結果多邊形的界限。  
  
 如果**字串**參數傳遞至此方法，然後將轉換成**float**或將會擲回`ArgumentException`。  
  
## <a name="examples"></a>範例  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geometry-instance"></a>A. 在一維幾何例項上，以參數值 < 0 呼叫 BufferWithCurves()  
 下列範例會傳回空白 `GeometryCollection` 執行個體：  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(-1).ToString(); 
 ```
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geometry-instance"></a>B. 在二維幾何例項上，以參數值 < 0 呼叫 BufferWithCurves()  
 下列範例會傳回具有負數緩衝的 `CurvePolygon` 執行個體：  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>C. 以參數值 < 0 呼叫 BufferWithCurves()，傳回空的 GeometryCollection  
 下列範例會顯示發生什麼事時*距離*參數等於-2:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 這**選取**陳述式會傳回`GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>D. 以參數值 = 0 呼叫 BufferWithCurves()  
 下列範例會傳回一份呼叫**幾何**執行個體：  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>E. 以極小的非零參數值呼叫 BufferWithCurves()  
 下列範例也會傳回一份呼叫**幾何**執行個體：  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 DECLARE @distance float = 1e-20; 
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>F. 以參數值 > 0 呼叫 BufferWithCurves()  
 下列範例會傳回 `CurvePolygon` 執行個體：  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
  
### <a name="g-passing-a-valid-string-parameter"></a>G. 傳遞有效的字串參數  
 下列範例會傳回與上述範例相同的 `CurvePolygon` 執行個體，但傳遞字串參數至方法：  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves('2').ToString();
 ```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>H. 傳遞無效的字串參數  
 下列範例會擲回錯誤：  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)' 
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 請注意，上述兩個範例傳遞字串常值至 `BufferWithCurves()` 方法。 第一個範例可行，因為字串常值可轉換為數值。 但是，第二個範例會擲回 `ArgumentException`。  
  
### <a name="i-calling-bufferwithcurves-on-multipoint-instance"></a>I. 在 MultiPoint 執行個體上呼叫 BufferWithCurves()  
 下列範例會傳回兩個 `GeometryCollection` 執行個體和一個 `CurvePolygon` 執行個體：  
  
```
 DECLARE @g geometry = 'MULTIPOINT((1 1),(1 4))'; 
 SELECT @g.BufferWithCurves(1).ToString(); 
 SELECT @g.BufferWithCurves(1.5).ToString(); 
 SELECT @g.BufferWithCurves(1.6).ToString();
 ```  
  
 前兩個**選取**陳述式會傳回`GeometryCollection`執行個體，因為參數*距離*小於或等於 1/2 的距離兩個點 (1 1) 和 (1 4)。 第三個**選取**陳述式會傳回`CurvePolygon`執行個體，因為緩衝的執行個體的兩個點 (1 1) 和 (1 4) 重疊。  
  
## <a name="see-also"></a>另請參閱  
 [幾何例項上擴充的方法](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
 
