---
description: StreamReadEnum
title: StreamReadEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
author: rothja
ms.author: jroth
ms.openlocfilehash: 1aa8ff80f02d84aaa69904d914e0e40da44da930
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441810"
---
# <a name="streamreadenum"></a>StreamReadEnum
指定是否應該從 [資料流程](../../../ado/reference/ado-api/stream-object-ado.md) 物件讀取整個資料流程或下一行。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|預設值。 從資料流程讀取所有位元組，從目前位置開始到 [EOS](../../../ado/reference/ado-api/eos-property.md) 標記。 這是唯一的有效 **StreamReadEnum** 值，具有二進位資料流程 ([類型](../../../ado/reference/ado-api/type-property-ado-stream.md) 為 **adTypeBinary**) 。|  
|**adReadLine**|-2|從資料流程讀取下一行 (由 [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) 屬性) 指定。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 相等  
 這些常數沒有 ADO/WFC 對等專案。  
  
## <a name="applies-to"></a>套用至  

:::row:::
    :::column:::
        [Read 方法](../../../ado/reference/ado-api/read-method.md)  
    :::column-end:::
    :::column:::
        [ReadText 方法](../../../ado/reference/ado-api/readtext-method.md)  
    :::column-end:::
:::row-end:::
