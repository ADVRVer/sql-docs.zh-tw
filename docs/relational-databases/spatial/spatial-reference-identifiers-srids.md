---
title: "空間參考識別碼 (SRID) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: spatial
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-spatial
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: eded5bfe9022cdbc8a0c991d5eb1d5f621aaf825
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="spatial-reference-identifiers-srids"></a>空間參考識別碼 (SRID)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] 每一個空間執行個體都有空間參考識別碼 (SRID)。 此 SRID 會對應到空間參考系統，此系統是以用於扁平表面對應或圓形表面對應的特定橢圓體為根據。  
  
> [!IMPORTANT]  
>  如需 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中引進之空間功能 (包括新的 SRID) 的詳細描述和範例，請下載技術白皮書： [New Spatial Features in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407)(SQL Server 2012 的新空間功能)。  
  
 空間資料行可包含具有不同 SRID 的物件。 但是，當針對資料使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 空間資料方法來執行作業時，只能使用具有相同 SRID 的空間執行個體。 衍生自兩個空間資料執行個體的任何空間方法結果只有在這兩個執行個體具有相同的 SRID (根據用來判斷執行個體座標的相同度量、資料和投射單位) 時，才是有效的。 最常見的 SRID 度量單位是公尺或平方公尺。  
  
 如果兩個空間執行個體沒有相同的 SRID，則執行個體上所用之 **geometry** 或 **geography** 資料類型方法的結果將會傳回 NULL。 例如，如果要讓下列述詞傳回非 NULL 的結果，兩個 **geometry** 執行個體 ( `geometry1` 和 `geometry2`) 必須有相同的 SRID：  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  空間參考識別系統是由 [歐洲石油探勘組織 (EPSG)](http://go.microsoft.com/fwlink/?LinkId=99349) 標準所定義，這是為了地圖製作、探勘和測地資料儲存所開發的一套標準。 這項標準的擁有者為石油生產者 (OGP) 探勘和定位委員會 (Oil and Gas Producers (OGP) Surveying and Positioning Committee)。  
  
## <a name="see-also"></a>另請參閱  
 [空間資料類型概觀](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
