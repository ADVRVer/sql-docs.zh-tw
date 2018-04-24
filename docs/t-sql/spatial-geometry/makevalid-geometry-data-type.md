---
title: MakeValid (geometry 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- MakeValid
- MakeValid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MakeValid (geometry Data Type)
ms.assetid: 38673010-ab77-4ebb-9c4d-b26b79e3b7ea
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: be92644c70770ec6b291814f35559c62b5a347b5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="makevalid-geometry-data-type"></a>MakeValid (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

將無效的 **geometry** 執行個體轉換成具有有效開放地理空間協會 (OGC) 類型的 **geometry** 執行個體。
  
## <a name="syntax"></a>語法  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geometry**  
  
 CLR 傳回類型：**SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 這個方法可能會造成 **geometry** 執行個體的類型變更，以及 **geometry** 執行個體的點稍微偏移。  
  
## <a name="examples"></a>範例  
 第一個範例會建立與自己重疊的無效 `LineString` 例項，並使用 `STIsValid()` 來確認它是無效的例項。 `STIsValid()` 會針對無效的例項傳回 0 的值。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 0);  
SELECT @g.STIsValid();  
```  
  
 第二個範例會使用 `MakeValid()` 讓此例項變成有效及測試看看此例項是否真正有效。 `STIsValid()` 會針對有效的例項傳回 1 的值。  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 第三個範例會確認此例項已做了哪些變更而成為有效的例項。  
  
```  
SELECT @g.ToString();  
```  
  
 在此範例中，當選取 `LineString` 例項時，值會當做有效的 `MultiLineString` 例項傳回。  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
 下列範例會將 CircularString 執行個體轉換成 Point 執行個體。  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 1 1, 1 1)';  
SELECT @g.MakeValid().ToString();  
```  
  
## <a name="see-also"></a>另請參閱  
 [STIsValid &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [幾何例項上擴充的方法](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

