---
title: SetSecureConnectionLevel 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 36b5efb8a1be107504cfcd7641b44c83924faa92
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81629599"
---
# <a name="configurationsetting-method---setsecureconnectionlevel"></a>ConfigurationSetting 方法 - SetSecureConnectionLevel
  設定報表伺服器的安全連接層級。  
  
## <a name="syntax"></a>語法  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>參數  
 *Level*  
 代表安全連接層級的整數值。  
  
 *HRESULT*  
 [out] 指出呼叫成功或失敗的值。  
  
## <a name="return-value"></a>傳回值  
 傳回 *HRESULT* ，指出方法呼叫成功或失敗。 值為 0 表示方法呼叫成功。 非零值則表示已發生錯誤。  
  
## <a name="remarks"></a>備註  
 呼叫時，報表伺服器的 SecureConnectionLevel 屬性會設定為指定的值。 值為 0 時，表示 TLS 為關閉狀態。 值大於或等於 1 時，表示 TLS 為開啟狀態。  
  
-   設定此值時，報表伺服器設定檔中的 SecureConnectionLevel 項目會變更，而且設定檔中的 **URLRoot** 項目會設定為使用 "https://" (如果指定的「層級」  大於或等於 1) 或 "http://" (如果指定的「層級」  為 0)。  
  
 在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]中，SecureConnectionLevel 會變成 on/off 開關，預設值為 0。 對於透過 SetSecureConnectionLevel 方法 API 所傳遞任何大於或等於 1 的值，都會將 TLS 視為開啟狀態，並且在 rsreportserver.config 檔案中據此設定組態屬性 SecureConnectionLevel。 基於回溯相容性，仍然允許使用值 2 和 3。  
  
## <a name="requirements"></a>需求  
 **命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [MSReportServer_ConfigurationSetting 成員](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
