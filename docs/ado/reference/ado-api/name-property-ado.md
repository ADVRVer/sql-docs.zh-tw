---
description: Name 屬性 (ADO)
title: 名稱屬性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Name
- Field20::Name
helpviewer_keywords:
- Name property [ADO]
ms.assetid: cfd0e29c-8310-44ab-85c3-5761184b865d
author: rothja
ms.author: jroth
ms.openlocfilehash: da88b8e5a98e7d3ae105cc6e826804158f4bf7c8
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774167"
---
# <a name="name-property-ado"></a>Name 屬性 (ADO)
指出物件的名稱。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回表示物件名稱的 **字串** 值。  
  
## <a name="remarks"></a>備註  
 使用 [ **名稱** ] 屬性可指派 **命令**的名稱，或取得命令、 **屬性**、 **欄位**或 **參數** 物件的名稱。  
  
 此值為 **命令** 物件的讀取/寫入，以及 **屬性** 物件的唯讀值。  
  
 若是 **Field** 物件， **名稱** 通常是唯讀的。 不過，對於附加至[記錄](./record-object-ado.md)之[Fields](./fields-collection-ado.md)集合的新**欄位**物件，只有在指定**欄位**的[Value](./value-property-ado.md)屬性，而且資料提供者已透過呼叫**Fields**集合的[Update](./update-method.md)方法成功加入新**欄位**之後，才會讀取/寫入**名稱**。  
  
 針對尚未附加至[Parameters](./parameters-collection-ado.md)集合的**參數**物件，[**名稱**] 屬性為 [讀取/寫入]。 針對附加的 **參數** 物件和所有其他物件，[ **名稱** ] 屬性是唯讀的。 名稱在集合中不一定是唯一的。  
  
 您可以藉由序數參考抓取物件的 **name** 屬性，之後您可以直接依名稱參考該物件。 例如，如果 `rstMain.Properties(20).Name` 產生 `Updatability` ，您接著可以將這個屬性稱為 `rstMain.Properties("Updatability")` 。  
  
## <a name="applies-to"></a>套用至  

:::row:::
    :::column:::
        [Command 物件 (ADO)](./command-object-ado.md)  
        [Field 物件](./field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter 物件](./parameter-object.md)  
        [Property 物件 (ADO)](./property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>另請參閱  
 [屬性和名稱屬性範例 (VB) ](./attributes-and-name-properties-example-vb.md)   
 [屬性和名稱屬性範例 (VC + +) ](./attributes-and-name-properties-example-vc.md)