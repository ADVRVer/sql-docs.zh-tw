---
title: Z (geography 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Z (geography Data Type)
- Z_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z method
ms.assetid: 9abc79c5-43c9-4cc2-b37f-d2ecdec7c234
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5f10566504e9f0f982175249f627ddba7106a4d4
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555731"
---
# <a name="z-geography-data-type"></a>Z (geography 資料類型)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  例項的 Z (高度) 值。 高度值的語意為使用者所定義。  
  
## <a name="syntax"></a>語法  
  
```  
  
.Z  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>傳回型別
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型：**float**  
  
 CLR 類型：**SqlDouble**  
  
## <a name="remarks"></a>備註  
 如果 **geography** 執行個體不是 point 以及對於未設定它的任何 **Point** 執行個體而言，這個屬性的值將會是 Null。  
  
 這個屬性是唯讀的。  
  
 Z 座標不會用於程式庫所做的任何計算，也不會透過任何程式庫計算來夾帶。  
  
## <a name="examples"></a>範例  
 下列範例會建立具有 Z (高度) 和 M (測量) 值的 `Point` 例項，並使用 `Z` 提取此例項的 Z 值。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>另請參閱  
 [地理執行個體上擴充的方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M &#40;geography 資料類型&#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [AsTextZM &#40;geography 資料類型&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
