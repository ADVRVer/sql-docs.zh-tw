---
description: Seek 方法
title: Seek 方法 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
author: rothja
ms.author: jroth
ms.openlocfilehash: 3325cbb2a1178be61167cc0291bf23564d1e84fb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777517"
---
# <a name="seek-method"></a>Seek 方法
搜尋 [記錄集](./recordset-object-ado.md) 的索引，以快速找出符合指定值的資料列，並將目前的資料列位置變更為該資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>參數  
 *KeyValues*  
 **Variant**值的陣列。 索引是由一或多個資料行所組成，陣列則包含要與每個對應資料行比較的值。  
  
 *SeekOption*  
 [SeekEnum](./seekenum.md)值，指定要在索引的資料行和對應的*KeyValues*之間進行的比較類型。  
  
## <a name="remarks"></a>備註  
 如果基礎提供者支援**記錄集**物件上的索引，請搭配[Index](./index-property.md)屬性使用**Seek**方法。 使用 [支援](./supports-method.md)** (adSeek) ** 方法來判斷基礎提供者是否支援 **搜尋**，並且 **支援 (adIndex) ** 方法來判斷提供者是否支援索引。  (例如， [Microsoft Jet 的 OLE DB 提供者](../../guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) 支援 **搜尋** 和 **索引**。 )   
  
 如果 **Seek** 找不到所需的資料列，就不會發生錯誤，而且資料列會定位於 **記錄集**的結尾。 執行此方法之前，請先將 **索引** 屬性設定為所需的索引。  
  
 只有伺服器端資料指標才支援這個方法。 當 **記錄集** 物件的 [CursorLocation](./cursorlocation-property-ado.md) 屬性值為 **adUseClient**時，不支援搜尋。  
  
 只有在使用[CommandTypeEnum](./commandtypeenum.md)值**AdCmdTableDirect**來開啟**記錄集**物件時，才能使用這個方法。  
  
## <a name="applies-to"></a>套用至  
 [Recordset 物件 (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [Seek 方法和 Index 屬性範例 (VB) ](./seek-method-and-index-property-example-vb.md)   
 [Seek 方法和 Index 屬性範例 (VC + +) ](./seek-method-and-index-property-example-vc.md)   
 [ (ADO) 的 Find 方法 ](./find-method-ado.md)   
 [Index 屬性](./index-property.md)