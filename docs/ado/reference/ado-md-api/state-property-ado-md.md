---
title: 狀態屬性 (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 812863395c2980f341ed2419eee1d9d661f19dd0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822158"
---
# <a name="state-property-ado-md"></a>State 屬性 (ADO MD)
表示資料格集的目前狀態。  
  
## <a name="return-values"></a>傳回值  
 傳回**長**整數，表示目前的狀況[資料格集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)物件，並處於唯讀狀態。 下列是有效值： **adStateClosed** (0) 和**adStateOpen** (1)。  
  
## <a name="remarks"></a>備註  
 若要使用[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)常數的名稱，您必須在專案中參考 ADO 型別程式庫。 請參閱[使用的 ADO 使用 ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)如需詳細資訊。  
  
## <a name="applies-to"></a>適用於  
 [Cellset 物件 (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>另請參閱  
 [Close 方法 (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Open 方法 (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
