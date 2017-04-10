---
title: "MultiLineString | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MultiLineString geometry 子類型 [SQL Server]"
  - "geometry 子類型 [SQL Server]"
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# MultiLineString
  **MultiLineString** 是零或多個 **geometry** 或 **geographyLineString** 執行個體的集合。  
  
## MultiLineString 執行個體  
 下圖顯示 **MultiLineString** 執行個體的範例。  
  
 ![幾何 MultiLineString 執行個體的範例](../../relational-databases/spatial/media/multilinestring.png "幾何 MultiLineString 執行個體的範例")  
  
 如本圖所示：  
  
-   圖 1 是簡單的 **MultiLineString** 執行個體，它的界限是其兩個 **LineString** 元素的四個端點。  
  
-   圖 2 是簡單的 **MultiLineString** 執行個體，因為只有 **LineString** 元素的端點才會相交。 界限是兩個非重疊的端點。  
  
-   圖 3 是非簡單的 **MultiLineString** 執行個體，因為它的其中一個 **LineString** 元素的內部會相交。 此 **MultiLineString** 執行個體的界限是這四個端點。  
  
-   圖 4 是非簡單、非封閉的 **MultiLineString** 執行個體。  
  
-   圖 5 是簡單、非封閉的 **MultiLineString**。 它不是封閉的，因為它的 **LineStrings** 元素不是封閉的。 因為任何 **LineStrings** 執行個體的內部都不相交，所以它是簡單的。  
  
-   圖 6 是簡單、封閉的 **MultiLineString** 執行個體。 它是封閉的，因為它的所有元素都是封閉的。 因為它的所有元素在內部都不相交，所以它是簡單的。  
  
### 已接受的執行個體  
 若要接受 **MultiLineString** 執行個體，則該執行個體必須是空的，或是僅由可接受的 **LineString** 執行個體組成。 如需已接受之 **LineString** 執行個體的詳細資訊，請參閱 [LineString](../../relational-databases/spatial/linestring.md)。 以下為已接受之 **MultiLineString** 執行個體的範例。  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 下列範例會擲回 `System.FormatException`，因為第二個 **LineString** 執行個體無效。  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### 有效的執行個體  
 **MultiLineString** 執行個體必須符合下列準則，才會是有效的：  
  
1.  組成 **MultiLineString** 執行個體的所有執行個體必須都是有效的 **LineString** 執行個體。  
  
2.  組成 **MultiLineString** 執行個體的任兩個 **LineString** 執行個體都不可在間隔上重疊。 **LineString** 執行個體只能在有限的點數內彼此交集或接觸，或是接觸其他 **LineString** 執行個體。  
  
 下列範例示範三個有效的 **MultiLineString** 執行個體和一個無效的 **MultiLineString** 執行個體。  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` 無效，因為第二個 **LineString** 執行個體與第一個 **LineString** 執行個體於間隔處重疊。 兩者以無限點數接觸。  
  
## 範例  
 下列範例會建立包含兩個具有 SRID 0 之 `LineString` 元素的簡單 `geometry``MultiLineString` 執行個體。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 若要使用不同的 SRID 來具現化這個執行個體，請使用 `STGeomFromText()` 或 `STMLineStringFromText()`。 您也可以使用 `Parse()`，然後修改 SRID，如下列範例所示。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## 另請參閱  
 [STLength &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STIsClosed &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [LineString](../../relational-databases/spatial/linestring.md)   
 [空間資料 &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  