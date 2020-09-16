---
description: SetUnattendedExecutionAccount 方法 (WMI MSReportServer_ConfigurationSetting)
title: SetUnattendedExecutionAccount 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5f65c36ae1f27039061642dba87ec79b6f81c7c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497921"
---
# <a name="configurationsetting-method---setunattendedexecutionaccount"></a>ConfigurationSetting 方法 - SetUnattendedExecutionAccount
  指定用來自動執行報表的帳戶。  
  
## <a name="syntax"></a>語法  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>參數  
 *使用者名稱*  
 要用於自動執行的 Windows 帳戶。  
  
 *密碼*  
 指定之帳戶的密碼。  
  
 *HRESULT*  
 [out] 指出呼叫成功或失敗的值。  
  
## <a name="return-value"></a>傳回值  
 傳回 *HRESULT* ，指出方法呼叫成功或失敗。 值為 0 表示方法呼叫成功。 非零值則表示已發生錯誤。  
  
## <a name="remarks"></a>備註  
 SetUnattendedExecutionAccount 方法不會驗證報表伺服器是否能夠登入成為指定的使用者。  
  
 在報表伺服器 Windows 服務的內容中，您無法使用 SetUnattendedExecutionAccount 方法來執行自動執行作業。  
  
## <a name="requirements"></a>需求  
 **命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [MSReportServer_ConfigurationSetting 成員](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
