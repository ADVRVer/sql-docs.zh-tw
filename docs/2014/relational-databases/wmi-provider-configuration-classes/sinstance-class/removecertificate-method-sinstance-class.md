---
title: RemoveCertificate 方法 （SInstance 類別） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- RemoveCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 7e5dbafa-a634-4617-9622-510514fce0ce
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d98cff84b93a13daec7be86dbc24b5fe9556f76c
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2018
ms.locfileid: "53366840"
---
# <a name="removecertificate-method-sinstance-class"></a>RemoveCertificate 方法 (SInstance 類別)
  從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體中移除目前的安全性憑證。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a>組件  
 *object*  
 代表 [執行個體上之伺服器設定的](sinstance-class.md) SInstance 類別 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]物件。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 uint32 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [設定伺服器網路通訊協定和網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
