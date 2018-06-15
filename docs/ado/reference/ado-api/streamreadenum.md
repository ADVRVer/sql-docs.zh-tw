---
title: StreamReadEnum |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6dca9f57838f938e225790e164870b1bec834bd3
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282527"
---
# <a name="streamreadenum"></a>StreamReadEnum
指定整個資料流或下一行是否應該從讀取[資料流](../../../ado/reference/ado-api/stream-object-ado.md)物件。  
  
|常數|ReplTest1|描述|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|預設值。 從資料流，從目前的位置讀取所有位元組，及更新版本為[EOS](../../../ado/reference/ado-api/eos-property.md)標記。 這是唯一有效**StreamReadEnum**二進位資料流的值 ([類型](../../../ado/reference/ado-api/type-property-ado-stream.md)是**adTypeBinary**)。|  
|**adReadLine**|-2|從資料流讀取下一行 (所指定[LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)屬性)。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 這些常數沒有 ADO/WFC 對等項目。  
  
## <a name="applies-to"></a>適用於  
  
|||  
|-|-|  
|[Read 方法](../../../ado/reference/ado-api/read-method.md)|[ReadText 方法](../../../ado/reference/ado-api/readtext-method.md)|
