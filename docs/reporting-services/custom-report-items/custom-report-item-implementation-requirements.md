---
title: 自訂報表項目實作需求 | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e25938d690d6e1046d1d0e75ae5a4952b05d4615
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "73594514"
---
# <a name="custom-report-item-implementation-requirements"></a>自訂報表項目實作需求
  本主題將討論開發和部署自訂報表項目的必要條件。  
  
## <a name="development-and-deployment-requirements"></a>開發和部署需求  
 為 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 開發自訂報表項目需要下列項目：  
  
-   對於執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 與 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的伺服器進行管理存取。  
  
-   已安裝 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 軟體開發套件 (SDK) 的 [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)] 或以上版本。  
  
-   存取 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文件集。  
  
-   熟悉 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中的元件製做與元件模型命名空間。  
  
## <a name="language-and-namespace-requirements"></a>語言與命名空間需求  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自訂報表項目完全支援 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]。 您可以使用所選的 .NET 相容語言來開發自訂報表項目。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 提供開發人員許多工具與功能，以簡化和加速程式碼撰寫、偵錯和測試的反覆循環，並使部署更加容易。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 包括 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 與 C# 編譯器及相關工具。  
  
-   自訂報表項目使用 **Microsoft.ReportDesigner** 和 <xref:Microsoft.ReportingServices.Interfaces> 命名空間。 這些是儲存在 Microsoft.ReportingServices.Designer.DLL 與 Microsoft.ReportingServices.Interfaces.DLL 組件中，是以 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的一部分來安裝。  
  
-   自訂報表項目設計階段元件需要從 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中的 <xref:System.ComponentModel> 命名空間實作介面。 <xref:System.ComponentModel> 記載於 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文件集中。  

## <a name="see-also"></a>另請參閱  
 [建立自訂報表項目執行階段元件](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [建立自訂報表項目設計階段元件](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [操作說明：部署自訂報表項目](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)   
 [自訂報表項目類別庫](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  
