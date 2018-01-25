---
title: "EnvelopeAngle (geography 資料類型) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs: TSQL
helpviewer_keywords: EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 692287aee372bf349cfa795e3b52c6e84c8e4f42
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回所傳回的點之間的最大角度`EnvelopeCenter()`中的點**geography**以度為單位的執行個體。  
  
 這**geography**資料類型方法可支援**FullGlobe**執行個體或大於半球的空間執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
EnvelopeAngle( )  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回型別： **float**  
  
 CLR 傳回類型： **SqlDouble**  
  
## <a name="remarks"></a>備註  
 這個方法會傳回中的點**geography**以度為單位的執行個體。 當搭配 EnvelopeCenter()，`EnvelopeAngle()`傳回的週框圓形**geography**執行個體。  
  
 在[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，這個方法已擴充到**FullGlobe**執行個體。  
  
 若要套用的半球限制`EnvelopeAngle()`中[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]已移除。 不過，對於角度大於 90 度的執行個體，則會傳回 180 度。 `EnvelopeAngle()`並不精確**geography**跨越超過一個半球的執行個體。  
  
## <a name="examples"></a>範例  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>另請參閱  
 [Geography 執行個體上的擴充的方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40; geography 資料類型 &#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  
