---
title: "RemoveURL 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RemoveURL 方法"
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# RemoveURL 方法 (WMI MSReportServer_ConfigurationSetting)
  移除針對報表伺服器所保留的 URL。 如果有多個需要移除的 URL，您就必須呼叫這個 API 來逐一進行此作業。  
  
## 語法  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## 參數  
 *應用程式*  
 要移除保留項目之應用程式的名稱。  
  
 *URLString*  
 保留項目的 URL。  
  
 *lcid*  
 要用於傳回之錯誤訊息的地區設定。  
  
 *錯誤*  
 [out] 發生之錯誤的描述。  
  
 *HRESULT*  
 [out] 指出呼叫成功或失敗的值。  
  
## 傳回值  
 傳回 *HRESULT* ，指出方法呼叫成功或失敗。 值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。  
  
## 備註  
 *UrlString* 不包含虛擬目錄名稱 - [SetVirtualDirectory 方法 &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md) 方法是針對該目的提供的。  
  
 呼叫 [ReserveURL](../../reporting-services/wmi-provider-library-reference/reserveurl-method-wmi-msreportserver-configurationsetting.md) 方法之前，您必須針對 *Application* 參數的 VirtualDirectory 組態屬性提供一個值。 您可以使用 [SetVirtualDirectory 方法 &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md) 方法來設定 VirtualDirectory 屬性。  
  
 如果 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供了 SSL 憑證，但是沒有其他 URL 需要它，就會移除此憑證。  
  
 這個方法會導致所有非組態應用程式網域在此作業期間進行硬式回收並停止。在此作業完成之後，應用程式網域就會重新啟動。  
  
## 需求  
 **命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## 請參閱＜  
 [MSReportServer_ConfigurationSetting 成員](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  