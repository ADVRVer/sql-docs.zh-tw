---
title: STGeomCollFromWKB (geography 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STGeomCollFromWKB (geography Data Type)
- STGeomCollFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMGeomCollFromWKB method
ms.assetid: bbed028c-9cd6-4236-b5e5-8e914a21f2e4
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7c9ed0d97c2bacd7891434dfeffe92a71cfc3709
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "33061937"
---
# <a name="stgeomcollfromwkb-geography-data-type"></a>STGeomCollFromWKB (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

從開放地理空間協會 (Open Geospatial Consortium，OGC) 已知的二進位 (well-known binary，WKB) 表示法傳回 **GeometryCollection** 執行個體。
  
## <a name="syntax"></a>語法  
  
```  
  
STGeomCollFromWKB ( 'WKB_geometrycollection' , SRID )  
```  
  
## <a name="arguments"></a>引數  
 *WKB_geometrycollection*  
 這是要傳回之 **GeometryCollection** 執行個體的 WKB 表示法。 *WKB_geometrycollection* 是 **varbinary(max)** 運算式。  
  
 *SRID*  
 這是 **int** 運算式，表示要傳回之 **GeometryCollection** 執行個體的空間參考識別碼 (Spatial Reference Identifier，SRID)。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geography**  
  
 CLR 傳回類型：**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 STGeomCollFromWKB() 傳回之 **geography** 執行個體的 OGC 類型會根據對應的 WKB 輸入而設定為 **GeometryCollection**、**MultiPolygon**、**MultiLineString** 或 **MultiPoint**。  
  
 如果輸入的格式不正確，這個方法將會擲回 **FormatException** 例外狀況。  
  
## <a name="examples"></a>範例  
 下列範例會使用 `STGeomCollFromWKB()` 建立 `geography` 例項。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomCollFromWKB(0x01070000000200000001010000007593180456965EC017D9CEF753D34740010200000002000000D7A3703D0A975EC08716D9CEF7D34740CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另請參閱  
 [OGC 靜態地理方法](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
