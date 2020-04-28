---
title: 軸集合（ADO MD） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Axes
- Cellset::Axes
helpviewer_keywords:
- Axes collection [ADO MD]
ms.assetid: 072fb21a-ec0f-4b02-9022-1cef3ad4bfff
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c06faf6327d60be823ce9d99215655b5badf5e3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "67947400"
---
# <a name="axes-collection-ado-md"></a>Axes 集合 (ADO MD)
包含定義儲存格集的[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)物件。  
  
## <a name="remarks"></a>備註  
 [[儲存格](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)] 物件包含一個 [**軸**] 集合。 一旦開啟**儲存格集**，此集合將包含至少一個**座標軸**。 如需如何使用**軸**物件的詳細說明，請參閱[Axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md)物件。  
  
> [!NOTE]
>  **儲存格集**的篩選軸不包含在**座標軸**集合中。 如需詳細資訊，請參閱[FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md)屬性。  
  
 **軸**是標準的 ADO 集合。 使用集合的屬性和方法，您可以執行下列動作：  
  
-   使用[Count](../../../ado/reference/ado-api/count-property-ado.md)屬性取得集合中的物件數目。  
  
-   使用預設[專案](../../../ado/reference/ado-api/item-property-ado.md)屬性，從集合中傳回物件。  
  
-   使用[Refresh](../../../ado/reference/ado-api/refresh-method-ado.md)方法，從提供者更新集合中的物件。  
  
 本章節包含下列主題。  
  
-   [屬性、方法和事件](../../../ado/reference/ado-md-api/axes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [格集範例（VB）](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Axis 物件 (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)
