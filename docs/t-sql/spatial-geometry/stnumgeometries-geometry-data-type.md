---
title: STNumGeometries (geometry 資料型別) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 13d898a97d78042d08a89d4e50d519c9695bf756
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回組成 **geometry** 執行個體的幾何數目。
  
## <a name="syntax"></a>語法  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**int**  
  
 CLR 傳回類型：**SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 如果 **geometry** 執行個體不是 **MultiPoint**、**MultiLineString**、**MultiPolygon** 或 **GeometryCollection** 執行個體，則傳回 1，如果 **geometry** 執行個體為空，則傳回 0。  
  
> [!NOTE]  
>  如果 **GeometryCollection** 擁有巢狀的空元素，則 `STNumGeometries()` 不會傳回 0。 雖然 **GeometryCollection** 執行個體中的元素是空的，但執行個體本身並不是空的集合。  
  
  

