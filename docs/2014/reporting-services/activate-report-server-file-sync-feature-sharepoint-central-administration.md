---
title: 啟用報表伺服器檔案同步處理功能，在 SharePoint 管理中心內 |Microsoft Docs
ms.prod: reporting-services-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/06/2017
ms.openlocfilehash: b56960b23370de3803f475c02aaee3b98ae491e4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63232913"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>在 SharePoint 管理中心啟動報表伺服器檔案同步處理功能

[ [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器檔案同步處理] 功能會利用 SharePoint 事件處理常式，同步處理報表伺服器目錄與文件庫中的項目。 當使用者經常直接上傳已發行的報表項目至 SharePoint 文件庫時，這項功能會很有幫助。 如果未啟用檔案同步處理功能，內容仍會同步處理，但是頻率會較低。  
  
安裝 SharePoint 產品的 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 增益集之後，可以在 SharePoint 網站管理中啟用檔案同步處理功能。  
  
這項功能可以在每個網站以手動方式啟用及停用，但不能在網站集合層級啟用及停用。  
  
## <a name="prerequisites"></a>先決條件  
 必須安裝適用於 SharePoint 的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集。 如果增益集未安裝，則不會顯示在 網站功能清單中檔案同步處理功能。  
  
 若要確認安裝，請檢視在 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **[控制台]** 中已安裝應用程式的清單。 如果已安裝 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集，請遵循本主題的指示來啟用報表伺服器同步處理功能。  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>在網站上啟用或停用報表伺服器檔案同步處理功能  
  
1.  從您的網站主要頁面上，按一下**站台動作**功能表，然後按一下**站台設定**。  
  
2.  在 **站台動作**，按一下**管理網站功能**。  
  
3.  在清單中找到 **[報表伺服器檔案同步處理]** 。  
  
4.  按一下 **[啟用]** 。  
  
> [!NOTE]  
>  若要停用報表伺服器檔案同步處理功能，您可以執行相同的程序，但是請按一下 [停用]  。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解報表組件&#40;報表產生器及 SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [在 SharePoint 中啟用報表伺服器和 Power View 整合功能](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [安裝或解除安裝 Reporting Services 增益集，適用於 SharePoint &#40;SharePoint 2010 和 SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [安裝或解除安裝 Reporting Services 增益集，適用於 SharePoint &#40;SharePoint 2010 和 SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
