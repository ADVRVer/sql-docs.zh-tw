---
title: "ListReservedURLs 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "ListReservedURLs 方法"
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# ListReservedURLs 方法 (WMI MSReportServer_ConfigurationSetting)
  列出針對報表伺服器上所有應用程式保留的 URL。  
  
## 語法  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## 參數  
 *Application[]*  
 [out] 具有 URL 保留項目的應用程式。  
  
 *UrlString[]*  
 [out] 已保留的 URL。  
  
 *Account[]*  
 [out] 與 URL 保留項目之帳戶相關聯的帳戶名稱。  
  
 *AccountSID[]*  
 [out] 與 URL 保留項目之帳戶相關聯的帳戶 SID。  
  
 *長度*  
 [out] 此方法所傳回之陣列的長度。  
  
 *HRESULT*  
 [out] 指出呼叫成功或失敗的值。  
  
## 傳回值  
 傳回 *HRESULT* ，指出方法呼叫成功或失敗。 值為 0 表示方法呼叫成功。錯誤碼則表示呼叫不成功。  
  
## 備註  
  
## 需求  
 **命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## 請參閱＜  
 [MSReportServer_ConfigurationSetting 成員](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  