---
title: 定義 Cube 階層屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b064db7ff0e496ea7a46085825afc202fced605
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62726357"
---
# <a name="define-cube-hierarchy-properties"></a>定義 Cube 階層屬性
  Cube 階層屬性可以讓您根據同一個資料庫維度，為 Cube 維度中的使用者自訂階層指定唯一設定。 下表描述 Cube 階層的屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|`Enabled`|決定是否為 Cube 維度啟用階層。|  
|`HierarchyID`|包含階層的唯一識別碼 (ID)。|  
|`OptimizedState`|決定套用至階層的最佳化層級。 此屬性可以有下列的值：<br /><br /> `FullyOptimized`:執行個體會建立階層的索引，以增進查詢效能。 這是預設值。<br /><br /> `NotOptimized`:執行個體不會建立其他索引。|  
|`Visible`|決定 Cube 階層的可見性。 預設值是 `True`。|  
  
## <a name="see-also"></a>另請參閱  
 [使用者階層](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
