---
title: "建立傳遞延伸模組程式庫 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 63b32f93-4bab-4b07-bd72-39a47aca1cda
caps.latest.revision: "36"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a2629cae0f289d1f7f496eee55826b105c52637f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="creating-a-delivery-extension-library"></a>建立傳遞延伸模組程式庫
  每個您建立的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組都應該指派到唯一的命名空間，並內建於程式庫或是組件檔中。 命名空間的正確名稱並不重要，但是它必須是唯一且未與其他延伸模組共用。 您應該為公司的傳遞延伸模組建立自己的唯一命名空間。  
  
 下列範例示範開始 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組的程式碼，這是使用包含傳遞介面與任何公用程式類別的命名空間。  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 編譯 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組時，您必須提供 Microsoft.ReportingServices.Interfaces.dll 的參考給編譯器，因為其中包含傳遞延伸模組介面與類別。 需要 <xref:Microsoft.ReportingServices.Interfaces> 命名空間實作 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 介面、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 介面等等。 例如，如果所有包含程式碼以實作用 C# 撰寫的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組之檔案，都在單一目錄中並且副檔名為 .cs，則會從該目錄發出下列命令，以編譯儲存在 CompanyName.ExtensionName.dll 中的檔案。  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 下列程式碼範例示範將用於副檔名為 .vb 之 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 檔案的命令。  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  您也可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 來設計、開發和建立傳遞延伸模組。 如需有關在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中開發組件的詳細資訊，請參閱 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文件集。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 延伸模組](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [實作傳遞延伸模組](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 延伸模組程式庫](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
