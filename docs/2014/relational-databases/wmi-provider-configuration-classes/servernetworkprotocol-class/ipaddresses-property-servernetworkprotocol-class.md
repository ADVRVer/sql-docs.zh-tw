---
title: IpAddresses 屬性 （ServerNetworkProtocol 類別） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- IpAddresses Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e7b2adf53bc6ebca14e2d3b4dc2cee248a4b6720
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2018
ms.locfileid: "53371330"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a>IpAddresses 屬性 (ServerNetworkProtocol 類別)
  取得與伺服器網路通訊協定相關聯的 IP 位址。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.IpAddresses [= value]  
```  
  
## <a name="parts"></a>組件  
 *object*  
 A`ServerNetworkProtocol`物件，表示執行個體所使用的網路通訊協定[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 陣列[ServerNetworkProtocolIPAdress 類別](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md)代表伺服器網路通訊協定支援的 IP 位址的物件。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [設定伺服器網路通訊協定和網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
