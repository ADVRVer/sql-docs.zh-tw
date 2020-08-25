---
description: LineSeparator 屬性 (ADO)
title: " (ADO) 的 LineSeparator 屬性 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
author: rothja
ms.author: jroth
ms.openlocfilehash: fe0976fda4a390f93f7d634fac9e1cbc52104b29
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774627"
---
# <a name="lineseparator-property-ado"></a>LineSeparator 屬性 (ADO)
表示要在文字 [資料流程](./stream-object-ado.md) 物件中當做行分隔符號使用的二進位字元。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回 [LineSeparatorsEnum](./lineseparatorsenum.md) 值，這個值表示 **資料流程**中使用的行分隔字元。 預設值為 **adCRLF**。  
  
## <a name="remarks"></a>備註  
 **LineSeparator** 是用來解讀讀取文字 **資料流程**內容時的行。 您可以使用 [SkipLine](./skipline-method.md) 方法略過程式程式碼。  
  
 **LineSeparator** 僅適用于文字 **資料流程** 物件， ([類型](./type-property-ado-stream.md) 為 **adTypeText**) 。 如果 **類型** 為 **adTypeBinary**，則會忽略這個屬性。  
  
## <a name="applies-to"></a>套用至  
 [Stream 物件 (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [Stream 物件 (ADO)](./stream-object-ado.md)