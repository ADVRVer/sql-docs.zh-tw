---
title: RSWindowsExtendedProtectionScenario 屬性 (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 67a43ee9150f68a55a9999eae5bc6e8d8fc970b2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63022444"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserverconfigurationsetting"></a>RSWindowsExtendedProtectionScenario 屬性 (WMI MSReportServer_ConfigurationSetting)
  傳回字串值，表示報表伺服器設定為允許的擴充保護案例。  
  
## <a name="syntax"></a>語法  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>備註  
 傳回字串值，表示報表伺服器設定為允許的擴充保護案例。 如果 WMI 提供者連線的報表伺服器不支援擴充保護，則會傳回 "" (空字串)。  
  
 下列清單顯示有效值：  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a>範例程式碼  
 [MSReportServer_ConfigurationSetting 類別](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>另請參閱  
 [RSWindowsExtendedProtectionLevel 屬性 &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [SetExtendedProtectionSettings 方法 &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md)   
 [Reporting Services 的驗證擴充保護](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer 設定檔](../report-server/rsreportserver-config-configuration-file.md)  
  
  
