---
title: FilterAxis 屬性 (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5015888cfafcce56c97f2369d418ed7be842dd28
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63295364"
---
# <a name="filteraxis-property-ado-md"></a>FilterAxis 屬性 (ADO MD)
指出目前的篩選資訊[資料格集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)。  
  
## <a name="return-values"></a>傳回值  
 傳回[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)物件，並處於唯讀狀態。  
  
## <a name="remarks"></a>備註  
 使用**FilterAxis**屬性傳回之維度用於配量的資料的相關資訊。 [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)屬性**軸**傳回交叉分析篩選器的維度數目。 這個座標軸通常會有一個資料列。  
  
 **軸**由**FilterAxis**並未包含在[軸](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)集合[Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)物件。  
  
## <a name="applies-to"></a>適用於  
 [Cellset 物件 (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>另請參閱  
 [Axis 物件 (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [維度物件 (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [DimensionCount 屬性 (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
