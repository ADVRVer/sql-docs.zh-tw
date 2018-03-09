---
title: "序數屬性 （ADO MD 儲存格） |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Cell::Ordinal
- Ordinal
helpviewer_keywords:
- Ordinal property [ADO MD]
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 70c8bb0793791873663c561ccafcdc37bcb37b8a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="ordinal-property-ado-md-cell"></a>序數屬性 （ADO MD 儲存格）
可唯一識別[儲存格](../../../ado/reference/ado-md-api/cell-object-ado-md.md)資料格集內的位置。  
  
## <a name="return-values"></a>傳回值  
 傳回**長**整數和處於唯讀狀態。  
  
## <a name="remarks"></a>備註  
 儲存格的序數值可唯一識別資料格集內的儲存格。 在概念上，方格的編號是在資料格集好像資料格集*p*-維陣列，其中*p*是數目[座標軸](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)。 方格的編號從列為主要順序中的零開始。 以下是計算資料格序數的公式：  
  
 儲存格的序數值可以搭配[項目](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)屬性[資料格集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)快速擷取物件[儲存格](../../../ado/reference/ado-md-api/cell-object-ado-md.md)。  
  
## <a name="applies-to"></a>適用於  
 [Cell 物件 (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>另請參閱  
 [軸範例 (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [資料格集物件 (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [項目屬性 （ADO MD 資料格集）](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [Ordinal 屬性 (ADO MD Position)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)
