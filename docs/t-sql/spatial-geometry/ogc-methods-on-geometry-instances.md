---
title: 幾何執行個體上的 OGC 方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- OGC Methods on Geometry Instances [SQL Server]
ms.assetid: c0c0f441-bf33-410c-9df0-544e3d05b944
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 025dd4b5d1bcd2cdf7682e5088c1d15470e5832c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ogc-methods-on-geometry-instances"></a>幾何例項上的 OGC 方法
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援幾何執行個體上的開放式地理空間協會 (Open Geospatial Consortium，OGC) 方法。  
  
 如需有關 OGC 規格的詳細資訊，請參閱下列主題：  
  
-   [OGC 規格，簡單特徵存取第一部 - 常見架構](http://go.microsoft.com/fwlink/?LinkId=93627)  
  
-   [OGC 規格，簡單特徵存取第二部 - SQL 選項](http://go.microsoft.com/fwlink/?LinkId=93628)  
  
## <a name="in-this-section"></a>本節內容  
  
-   [STArea](../../t-sql/spatial-geometry/starea-geometry-data-type.md)  
  
-   [STAsBinary](../../t-sql/spatial-geometry/stasbinary-geometry-data-type.md)  
  
-   [STAsText](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)  
  
-   [STBoundary](../../t-sql/spatial-geometry/stboundary-geometry-data-type.md)  
  
-   [STBuffer](../../t-sql/spatial-geometry/stbuffer-geometry-data-type.md)  
  
-   [STCentroid](../../t-sql/spatial-geometry/stcentroid-geometry-data-type.md)  
  
-   [STContains](../../t-sql/spatial-geometry/stcontains-geometry-data-type.md)  
  
-   [STConvexHull](../../t-sql/spatial-geometry/stconvexhull-geometry-data-type.md)  
  
-   [STCrosses](../../t-sql/spatial-geometry/stcrosses-geometry-data-type.md)  
  
-   [STCurveN &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/stcurven-geometry-data-type.md)  
  
-   [STCurveToLine &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/stcurvetoline-geometry-data-type.md)  
  
-   [STDifference](../../t-sql/spatial-geometry/stdifference-geometry-data-type.md)  
  
-   [STDimension](../../t-sql/spatial-geometry/stdimension-geometry-data-type.md)  
  
-   [STDisjoint](../../t-sql/spatial-geometry/stdisjoint-geometry-data-type.md)  
  
-   [STDistance](../../t-sql/spatial-geometry/stdistance-geometry-data-type.md)  
  
-   [STEndpoint](../../t-sql/spatial-geometry/stendpoint-geometry-data-type.md)  
  
-   [STEnvelope](../../t-sql/spatial-geometry/stenvelope-geometry-data-type.md)  
  
-   [STEquals](../../t-sql/spatial-geometry/stequals-geometry-data-type.md)  
  
-   [STExteriorRing](../../t-sql/spatial-geometry/stexteriorring-geometry-data-type.md)  
  
-   [STGeometryN](../../t-sql/spatial-geometry/stgeometryn-geometry-data-type.md)  
  
-   [STGeometryType](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)  
  
-   [STInteriorRingN](../../t-sql/spatial-geometry/stinteriorringn-geometry-data-type.md)  
  
-   [STIntersection](../../t-sql/spatial-geometry/stintersection-geometry-data-type.md)  
  
-   [STIntersects](../../t-sql/spatial-geometry/stintersects-geometry-data-type.md)  
  
-   [STIsClosed](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)  
  
-   [STIsEmpty](../../t-sql/spatial-geometry/stisempty-geometry-data-type.md)  
  
-   [STIsRing](../../t-sql/spatial-geometry/stisring-geometry-data-type.md)  
  
-   [STIsSimple](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md)  
  
-   [STIsValid](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
-   [STLength](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)  
  
-   [STNumCurves &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/stnumcurves-geometry-data-type.md)  
  
-   [STNumGeometries](../../t-sql/spatial-geometry/stnumgeometries-geometry-data-type.md)  
  
-   [STNumInteriorRing](../../t-sql/spatial-geometry/stnuminteriorring-geometry-data-type.md)  
  
-   [STNumPoints](../../t-sql/spatial-geometry/stnumpoints-geometry-data-type.md)  
  
-   [STOverlaps](../../t-sql/spatial-geometry/stoverlaps-geometry-data-type.md)  
  
-   [STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md)  
  
-   [STPointOnSurface](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)  
  
-   [STRelate](../../t-sql/spatial-geometry/strelate-geometry-data-type.md)  
  
-   [STSrid](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)  
  
-   [STStartPoint](../../t-sql/spatial-geometry/ststartpoint-geometry-data-type.md)  
  
-   [STSymDifference](../../t-sql/spatial-geometry/stsymdifference-geometry-data-type.md)  
  
-   [STTouches](../../t-sql/spatial-geometry/sttouches-geometry-data-type.md)  
  
-   [STUnion](../../t-sql/spatial-geometry/stunion-geometry-data-type.md)  
  
-   [STWithin](../../t-sql/spatial-geometry/stwithin-geometry-data-type.md)  
  
-   [STX](../../t-sql/spatial-geometry/stx-geometry-data-type.md)  
  
-   [STY](../../t-sql/spatial-geometry/sty-geometry-data-type.md)  
  
## <a name="see-also"></a>另請參閱  
 [幾何執行個體上擴充的方法](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [OGC 靜態幾何方法](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)   
 [擴充的靜態幾何方法](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  
