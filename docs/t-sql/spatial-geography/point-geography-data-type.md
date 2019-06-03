---
title: Point (geography 資料型別) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point method
- Point (geography Data Type)
ms.assetid: 0dc6f422-7aae-4016-b7f4-3289fa8f989c
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: ddd506ca3e78dd4ad5a12cfb108ca539e094cb4e
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2019
ms.locfileid: "65938005"
---
# <a name="point-geography-data-type"></a>Point (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

建構 **geography** 執行個體，這個執行個體會根據其緯度和經度值與空間參考識別碼 (SRID) 來表示 **Point** 執行個體。
  
## <a name="syntax"></a>語法  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
## <a name="arguments"></a>引數  
 *Lat*  
 這是 **float** 運算式，代表所要產生之 **Point** 的 X 座標。  
  
 *Long*  
 這是 **float** 運算式，代表所要產生之 **Point** 的 Y 座標。 如需有關有效緯度和經度值的詳細資訊，請參閱 [Point](../../relational-databases/spatial/point.md)。  
  
 *SRID*  
 這是 **int** 運算式，表示要傳回之 **geography** 執行個體的 SRID。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geography**  
  
 CLR 傳回型別：**SqlGeography**  
  
> [!NOTE]  
>  引數的點 (geography 資料類型) 的方法有相較於 WKT 為反轉的座標。  
  
## <a name="examples"></a>範例  
 下列範例會使用 `Point()` 建立 `geography` 例項。  
  
```  
DECLARE @g geography;   
SET @g = geography::Point(47.65100, -122.34900, 4326)  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另請參閱  
 [擴充的靜態地理方法](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
