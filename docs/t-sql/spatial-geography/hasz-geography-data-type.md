---
title: HasZ (geography 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 05/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HasZ
- HasZ_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- HasZ geography
ms.assetid: 4c5e1669-a987-4dda-9ebf-f573ce615c34
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 8aae17057d9b4b114ed7ad03fd7e29ad61f127b3
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "67930249"
---
# <a name="hasz-geography-data-type"></a>HasZ (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  如果空間物件至少包含一個 Z 值，則傳回 1 (true)，否則傳回 0 (false)。  
  
## <a name="syntax"></a>語法  
  
```  
  
.HasZ  
```  
  
## <a name="return-types"></a>傳回型別  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**bit**  
  
 CLR 傳回類型：**Boolean**  
  
## <a name="remarks"></a>備註  
  
## <a name="examples"></a>範例  
  
```sql  
DECLARE @p GEOGRAPHY = 'Point(1 1 1 1)'  
SELECT @p.HasZ   
--Returns: 1 (true)  
```  
  
## <a name="see-also"></a>另請參閱  
 [地理執行個體上擴充的方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [Z &#40;geography 資料類型&#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
