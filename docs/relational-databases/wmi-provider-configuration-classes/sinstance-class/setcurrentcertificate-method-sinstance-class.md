---
title: SetCurrentCertificate 方法（SInstance）
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetCurrentCertificate Method (SInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 7349fb87-b973-4160-a2be-cab73abf5b31
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dadbbcb0f59dda924a0cc01826066e7d9f077189
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "73659061"
---
# <a name="setcurrentcertificate-method-sinstance-class"></a>SetCurrentCertificate 方法 (SInstance 類別)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  設定目前的安全性憑證。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.SetCurrentCertificate(SHA)  
```  
  
## <a name="parts"></a>組件  
 *目標*  
 代表實例上之[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]伺服器設定的[SInstance 類別](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md)物件。  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*SHA*|指定目前安全性憑證的字串值。|  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 **Uint32**值，如果已成功修改服務，則為0，如果不支援要求則為1，以及其他指示錯誤的任何數位。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
