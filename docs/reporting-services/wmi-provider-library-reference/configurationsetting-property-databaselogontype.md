---
title: DatabaseLogonType 屬性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DatabaseLogonType
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 078c430e2300a0b80f85357f9f962e8e2dd72838
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "65570910"
---
# <a name="configurationsetting-property---databaselogontype"></a>ConfigurationSetting 屬性 - DatabaseLogonType
  指定報表伺服器會使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 服務帳戶、Windows 使用者帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入來存取報表伺服器資料庫。 唯讀。  
  
## <a name="syntax"></a>語法  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>屬性值  
 代表登入類型的 **integer** 物件。  
  
## <a name="example-code"></a>範例程式碼  
 [MSReportServer_ConfigurationSetting 類別](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>備註  
 值為：  
  
-   0 代表 Windows 登入  
  
-   1 代表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入  
  
-   2 代表要當做服務登入  
  
 如果您指定了 0 (Windows)，就必須將 [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) 屬性中的值設定為對應的有效 Windows 使用者帳戶。  
  
 如果您指定 1 (SQL Server)，請確定 [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) 的值對應至有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。  
  
 如果您指定了 2 (Windows 服務)，報表伺服器就會使用 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 帳戶和 Windows 服務帳戶來存取報表伺服器資料庫。 會忽略 DatabaseLogonAccount 屬性。  
  
## <a name="requirements"></a>需求  
 **命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [MSReportServer_ConfigurationSetting 成員](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
