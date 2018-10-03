---
title: NamedParameters 屬性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c63fb598630a30fd2616722146bb6737f17b82b5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760406"
---
# <a name="namedparameters-property-ado"></a>NamedParameters 屬性 (ADO)
指出參數名稱是否應該傳遞給提供者。  
  
## <a name="remarks"></a>備註  
 這個屬性，則為 true 時，ADO 值傳遞給**名稱**屬性中的每個參數**參數**集合[命令物件](../../../ado/reference/ado-api/command-object-ado.md)。 提供者會使用參數名稱來比對中的參數**CommandText**或是**CommandStream**屬性。 如果這個屬性為 false （預設值），則會忽略參數名稱和提供者會使用參數的順序來比對中的參數值**CommandText**或是**CommandStream**屬性。  
  
## <a name="applies-to"></a>適用於  
 [Command 物件 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [CommandText 屬性 (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandStream 屬性 (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Parameters 集合 (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
