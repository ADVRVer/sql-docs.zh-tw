---
title: STGeomFromText (geography 資料型別) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeomFromText (geography Data Type)
- STGeomFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full globe
- STGeomFromText method
ms.assetid: 3717987b-77d8-4ccf-a1db-5a8016ac1083
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 6fc2c33daffe05ad996f62f07ae05dd098980e59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936849"
---
# <a name="stgeomfromtext-geography-data-type"></a>STGeomFromText (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

從開放地理空間協會 (OGC) 的已知的文字 (WKT) 表示法傳回 **geography** 執行個體，經由此執行個體夾帶的任何 Z (高度) 和 M (測量) 值來擴充。
  
這個 **geography** 資料類型方法可支援 **FullGlobe** 執行個體或大於半球的空間執行個體。
  
## <a name="syntax"></a>語法  
  
```  
  
STGeomFromText ( 'geography_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>引數  
 *geography_tagged_text*  
 傳回之 **geography** 執行個體的 WKT 表示法。 *geography_tagged_text* 是一個 **nvarchar(max)** 運算式。  
  
 *SRID*  
 這是 **int** 運算式，表示要傳回之 **geography** 執行個體的空間參考識別碼 (SRID)。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geography**  
  
 CLR 傳回型別：**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 STGeomFromText() 傳回之 **geography** 執行個體的 OGC 型別會設定為對應的 WKT 輸入。  
  
 如果輸入包含對蹠邊緣，這個方法會擲回 **ArgumentException**。  
  
## <a name="examples"></a>範例  
 下列範例會使用 `STGeomFromText()` 建立 `geography` 例項。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另請參閱  
 [OGC 靜態地理方法](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
