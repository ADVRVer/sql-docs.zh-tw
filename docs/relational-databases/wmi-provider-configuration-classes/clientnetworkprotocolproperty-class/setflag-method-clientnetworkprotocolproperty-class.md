---
title: SetFlag 方法 （ClientNetworkProtocolProperty 類別） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetFlag Method (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetFlag method
ms.assetid: 0407520f-2f84-4f68-b2b7-429697286c1b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8c16ae47f80a9d349090684bf7e9c7faf1dca641
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68035308"
---
# <a name="setflag-method-clientnetworkprotocolproperty-class"></a>SetFlag 方法 (ClientNetworkProtocolProperty 類別)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  設定所參考之目前屬性的旗標[PropertyIdx 屬性 （ClientNetworkProtocolProperty 類別）](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md)值。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.SetFlag(BoolValue) [=]  
```  
  
## <a name="parts"></a>組件  
 *object*  
 A [ClientNetworkProtocolProperty 類別](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md)物件，表示屬性所使用之網路通訊協定[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]用戶端。  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*BoolValue*|指定旗標之新值的布林值。|  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 A **uint32**值，也就是 0，如果已成功修改此服務，不支援要求，則為 1，而其他數值則表示錯誤。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [設定用戶端通訊協定](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
