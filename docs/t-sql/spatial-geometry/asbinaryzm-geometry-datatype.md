---
title: "AsBinaryZM (geometry 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 08/03/2017
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
helpviewer_keywords: AsBinaryZM geometry
ms.assetid: 5eae2872-adca-4b8f-8b04-4ee91ced98f1
caps.latest.revision: "6"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0c250cae7bce041e858b71b21f0f0a140560604
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2018
---
# <a name="asbinaryzm-geometry-datatype"></a>AsBinaryZM (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

傳回開放式地理空間協會 (OGC) 已知二進位 (well-known binary，WKB) 表示**幾何**執行個體夾帶任何**Z** （高度） 和**M** （量值）執行個體所夾帶的值。
  
## <a name="syntax"></a>語法  
  
```  
  
.AsBinaryZM()  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別： **varbinary （max)**  
  
 CLR 傳回類型： **SqlBytes**  
  
## <a name="remarks"></a>備註  
  
## <a name="examples"></a>範例  
  
```sql  
DECLARE @g1 GEOMETRY = 'Point(1 1 2 3)';  
  
SELECT @g1.STAsBinary();  
-- Returns: 0x0101000000000000000000F03F000000000000F03F  
  
SELECT @g1.AsBinaryZM();  
--Returns: 0x01B90B0000000000000000F03F000000000000F03F00000000000000400000000000000840  
```  
  
## <a name="see-also"></a>請參閱  
 [幾何例項上擴充的方法](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [M &#40; geometry 資料類型 &#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [Z &#40; geometry 資料類型 &#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  

