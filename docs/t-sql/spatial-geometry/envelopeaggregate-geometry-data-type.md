---
title: "EnvelopeAggregate (geometry 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAggregate method (geometry)
ms.assetid: c4c15abe-0fe9-441d-9d42-6572e264869c
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f6bf9a42f6d41973f2abed3377c5a311271e106f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="envelopeaggregate-geometry-data-type"></a>EnvelopeAggregate (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

傳回一組指定的週框方塊**幾何**物件。
  
## <a name="syntax"></a>語法  
  
```  
  
EnvelopeAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>引數  
 *geometry_operand*  
 是**幾何**類型資料表資料行代表一組**幾何**物件。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別：**幾何**  
  
## <a name="exceptions"></a>例外狀況  
 輸入的值無效時，會擲回 `FormatException`。 請參閱[STIsValid &#40; geometry 資料類型 &#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
## <a name="remarks"></a>備註  
 方法會傳回**null**當輸入是空的或輸入具有不同的 Srid。 請參閱[空間參考識別碼 &#40;Srid &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 方法會忽略**null**輸入。  
  
> [!NOTE]  
>  方法會傳回**null**如果所有輸入的值為**null**。  
  
## <a name="examples"></a>範例  
 下列範例會傳回資料表變數資料行中物件集的週框方塊。  
  
 ```
 -- Setup table variable for EnvelopeAggregate example 
DECLARE @Geom TABLE 
( 
shape geometry, 
shapeType nvarchar(50) 
) 
INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'), 
('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle'); 
-- Perform EnvelopeAggregate on @Geom.shape column 
SELECT geometry::EnvelopeAggregate(shape).ToString() 
FROM @Geom;
 ```  
  
## <a name="see-also"></a>另請參閱  
 [擴充的靜態幾何方法](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


