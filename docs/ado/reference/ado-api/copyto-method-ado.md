---
description: CopyTo 方法 (ADO)
title: " (ADO) 的 CopyTo 方法 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_CopyTo
- _Stream::CopyTo
helpviewer_keywords:
- CopyTo method [ADO]
ms.assetid: b4aa5714-916b-48b8-8b09-cc2708379602
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bbb394810ebbfe8d8c0e1d598641a1e77e7d204
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974549"
---
# <a name="copyto-method-ado"></a>CopyTo 方法 (ADO)
根據[資料流程](./stream-object-ado.md)中的[類型](./type-property-ado-stream.md)) ，將指定的字元數或位元組數 (複製到另一個**資料流程**物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
Stream.CopyTo DestStream, NumChars  
```  
  
#### <a name="parameters"></a>參數  
 *DestStream*  
 物件變數值，包含開啟之 **資料流程** 物件的參考。 目前的**資料流程**會複製到*DestStream*所指定的目的地**資料流程**。 目的地 **資料流程** 必須已開啟。 如果沒有，就會發生執行階段錯誤。  
  
> [!NOTE]
>  *DestStream*參數可能不是**stream**物件的 proxy，因為這需要存取**資料流程**物件上無法遠端處理至用戶端的私用介面。  
  
 *NumChars*  
 選擇性。 **整數**值，指定要從來源**資料流程**中目前位置複製到目的**資料流程**的位元組數或字元數。 預設值為-1，指定將所有字元或位元組從目前位置複製到 [EOS](./eos-property.md)。  
  
## <a name="remarks"></a>備註  
 這個方法會複製指定的字元數或位元組數，從 [position](./position-property-ado.md) 屬性指定的目前位置開始。 如果指定的數目超過 **eos**的可用位元組數，則只會複製目前位置到 **eos** 的字元或位元組。 如果 *NumChars* 的值為-1 或省略，則會複製從目前位置開始的所有字元或位元組。  
  
 如果目的地資料流程中有現有的字元或位元組，則在複製結束的點之後的所有內容都會保留，且不會被截斷。 **位置** 會變成緊接最後一個位元組複製後的位元組。 如果您想要截斷這些位元組，請呼叫 [SetEOS](./seteos-method.md)。  
  
 **CopyTo**應該用來將資料複製到與來源**資料流程**相同類型的目的地**資料流程** (其**Type**屬性設定同時為**adTypeText**或**adTypeBinary**) 。 針對文字**資料流程**物件，您可以變更目的地**資料流程**的[字元集](./charset-property-ado.md)屬性設定，以從一個字元集轉換成另一個字元集。 此外，文字 **資料流程** 物件可以成功複製到二進位 **資料流程** 物件中，但無法將二進位 **資料流程** 物件複製到文字 **資料流程** 物件中。  
  
## <a name="applies-to"></a>套用至  
 [Stream 物件 (ADO)](./stream-object-ado.md)