---
title: IsNull (geometry 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7cb1cccba4c880fd2e92d707e51c8c4e324fba9c
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555640"
---
# <a name="isnull-geometry-data-type"></a>IsNull (geometry 資料類型)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

**geometry** 執行個體的類型為 Null。 如果執行個體不是 Null，就會傳回 0。
  
## <a name="syntax"></a>語法  
  
```  
.IsNull  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>傳回型別
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型：**bit**  
  
 CLR 類型：**SqlBoolean**  
  
## <a name="remarks"></a>備註  
 `IsNull` 可用來測試 **geometry** 執行個體是否為 Null。 如果執行個體不是 Null，`IsNull` 就會傳回 0，但是，如果執行個體為 Null，則會傳回 Null。  
  
 這個方法主要是由 SQL Server 基礎結構所使用；不建議您使用 `IsNull` 來測試執行個體是否為 Null。  
  

## <a name="see-also"></a>另請參閱  
 [幾何例項上擴充的方法](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

