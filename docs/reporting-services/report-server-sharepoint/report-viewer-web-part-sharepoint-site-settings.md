---
title: 報表檢視器網頁組件的 SharePoint 網站設定 - SSRS | Microsoft Docs
ms.date: 10/31/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server-sharepoint
ms.suite: ''
ms.topic: conceptual
author: jt000
ms.author: jasontre
ms.openlocfilehash: f39ac00241bd1c4a26b79766a7bc37865ef11181
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43281866"
---
# <a name="sharepoint-site-settings-for-the-report-viewer-web-part---reporting-services"></a>報表檢視器網頁組件的 SharePoint 網站設定 - Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

報表檢視器網頁組件中有一些可設定的值。 網站管理員可以在 SharePoint 網站設定頁面上啟用及停用這些設定。 請注意，每個網站有各自的設定。 此外，重新安裝報表檢視器網頁組件之後，不會重設這些設定。

## <a name="accessing-the-site-settings-page"></a>存取網站設定頁面

若要存取網站設定：

1. 在 SharePoint 網站中，選取左上方的**齒輪**圖示，然後選取 [網站設定]。

    ![從齒輪圖示開啟網站設定。](media/sharepoint-site-settings.png)

2. 在 [Reporting Services] 網站設定群組中，按一下 [Report Viewer Web Part Settings] \(報表檢視器網頁組件設定)。

    > [!NOTE]
    > 您也可以直接巡覽至 `<site>/_layouts/15/ReportViewerWebPart/ReportViewerWebPartSettings.aspx` 來到達網站設定

## <a name="report-viewer-web-part-settings"></a>報表檢視器網頁組件設定

|設定|註解|  
|-------------|--------------|  
|收集使用量資料|允許將錯誤和使用方式資訊傳送至 Microsoft，以協助改善我們的產品。 如需 Microsoft 錯誤報告資料收集原則，請參閱 [Microsoft SQL Server 隱私權聲明](http://go.microsoft.com/fwlink/?LinkID=868444)。|  
|啟用報表的可存取性中繼資料|設定已轉譯報表的 [`AccessibleTablix` 裝置資訊](../html-device-information-settings.md)。| 
