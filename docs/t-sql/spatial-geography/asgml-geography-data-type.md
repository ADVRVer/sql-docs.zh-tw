---
title: "AsGml (geography 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AsGml_(geography_Data_Type)_TSQL
- AsGml
- AsGml_TSQL
- AsGml (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- AsGml method
ms.assetid: 67795c64-d8d3-48dc-93ef-3c8a9274deb6
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f5c13754e9d889245e667dcf377ee158fb500aa
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
#  <a name="asgml---geography-data-type"></a>AsGml-geography 資料類型
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回的地理標記語言 (GML) 表示**geography**執行個體。  
  
 如需有關地理標記語言的詳細資訊，請參閱開放式地理空間協會規格： [OGC 規格，地理標記語言。](http://go.microsoft.com/fwlink/?LinkId=93629)  
  
## <a name="syntax"></a>語法  
  
```  
  
.AsGml ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別： **xml**  
  
 CLR 傳回類型： **SqlXml**  
  
## <a name="remarks"></a>備註  
  
## <a name="examples"></a>範例  
 下列範例會建立 `LineString` 例項，並使用 `AsGML()` 傳回此例項的 GML 描述。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.AsGml();  
```  
  
 這個方法會傳回 `LineString` 例項形式的描述。  
  
```  
<LineString xmlns="http://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Geography 執行個體上的擴充的方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
