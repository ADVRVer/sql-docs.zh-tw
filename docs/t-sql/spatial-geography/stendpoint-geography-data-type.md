---
title: STEndpoint (geography 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STEndpoint (geography Data Type)
- STEndpoint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STEndpoint method
ms.assetid: 8974cd07-8ec4-4126-8fc2-fdcf322ccedd
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 5202c1c61b7d7531737de828de935a14289a902d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936990"
---
# <a name="stendpoint-geography-data-type"></a>STEndpoint (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回 **geography** 執行個體的終點。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STEndPoint ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geography**  
  
 CLR 傳回型別：**SqlGeography**  
  
 開放式地理空間協會 (OGC) 類型：**點**  
  
## <a name="remarks"></a>Remarks  
 STEndPoint() 相當於 [STPointN](../../t-sql/spatial-geography/stpointn-geography-data-type.md)`(x.STNumPoints``())`。  
  
 這個方法如果在空的 **geography** 執行個體上呼叫，就會傳回 Null。  
  
## <a name="examples"></a>範例  
 下列範例會建立具有 `LineString` 的 `STGeomFromText()` 例項，並使用 `STEndpoint()` 來擷取 `LineString` 的終點。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STEndPoint().ToString();  
```  
  
## <a name="see-also"></a>另請參閱  
 [地理例項上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
