---
title: SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
caps.latest.revision: 11
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 20a3b086aeb2a2474f7bfb200c5d3f389bfa50ba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36135063"
---
# <a name="setvirtualdirectory-method-wmi-msreportserverconfigurationsetting"></a>SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting)
  針對給定的應用程式設定虛擬目錄的名稱。  
  
## <a name="syntax"></a>語法  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>參數  
 *應用程式*  
 要設定虛擬目錄之應用程式的名稱。  
  
 *VirtualDirectory*  
 虛擬目錄的名稱。  
  
 *lcid*  
 虛擬目錄的地區設定識別碼。  
  
 *錯誤*  
 [out] 發生之錯誤的描述。  
  
 *HRESULT*  
 [out] 指出呼叫成功或失敗的值。  
  
## <a name="return-value"></a>傳回值  
 傳回 *HRESULT* ，指出方法呼叫成功或失敗。 值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。  
  
## <a name="remarks"></a>備註  
 應用程式只能針對所有 URL 保留項目設有一個虛擬目錄名稱。  
  
 VirtualDirectory 必須符合虛擬目錄的命名慣例。 VirtualDirectory 不得為空字串或空白。  
  
 更新 \Configuration\URLReservations\Application\VirtualDirectory 元素的值。 即使尚未建立任何 URL 保留項目，也會成功。  
  
## <a name="requirements"></a>需求  
 **命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [MSReportServer_ConfigurationSetting 成員](msreportserver-configurationsetting-members.md)  
  
  