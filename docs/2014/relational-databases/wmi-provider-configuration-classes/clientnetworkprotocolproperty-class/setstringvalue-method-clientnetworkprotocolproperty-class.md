---
title: SetStringValue 方法 （ClientNetworkProtocolProperty 類別） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetStringValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 88d67b22-0eea-48c9-ab73-e0b4907953df
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2107c4cd3bfdd76d1adeaa00127a1fea4784001e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48071940"
---
# <a name="setstringvalue-method-clientnetworkprotocolproperty-class"></a>SetStringValue 方法 (ClientNetworkProtocolProperty 類別)
  設定所參考之目前屬性的字串值[PropertyIdx 屬性 （ClientNetworkProtocolProperty 類別）](clientnetworkprotocolproperty-class.md)值。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a>組件  
 *object*  
 A [ClientNetworkProtocolProperty 類別](clientnetworkprotocolproperty-class.md)物件，表示屬性所使用之網路通訊協定[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]用戶端。  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*strValue*|指定目前屬性之新值的字串值。|  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 `uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [設定用戶端通訊協定](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
