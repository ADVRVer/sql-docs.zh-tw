---
title: "GetReportServerUrls 方法 (WMI MSReportServer_Instance) | Microsoft Docs"
ms.custom: 
ms.date: 06/09/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: wmi-provider-library-reference
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
caps.latest.revision: "12"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fb88837f3c9393c561e65c13656bb0e87a516325
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="msreportserverinstance-methods---getreportserverurls"></a>MSReportServer_Instance 方法 - GetReportServerUrls
  傳回使用者可用來存取報表伺服器和 [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]的 URL 清單。  
  
## <a name="syntax"></a>語法  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a>參數  
 *ApplicationName[]*  
 包含已安裝之應用程式的陣列。 值為 **ReportServerWebService** 或 **ReportServerWebApp**。  
  
 *URLs[]*  
 包含成功註冊之 URL 的陣列。  
  
 *長度*  
 包含傳回之陣列長度的整數值。  
  
 *HRESULT*  
 表示成功的值或錯誤碼。  
  
## <a name="return-values"></a>傳回值  
  
## <a name="remarks"></a>Remarks  
 WMI 管理物件所公開的方法是透過 InvokeMethod 函數呼叫的。 如需詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI 文件集中的＜針對管理物件執行方法＞。  
  
## <a name="requirements"></a>需求  
 **命名空間：** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [MSReportServer_ConfigurationSetting 成員](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
