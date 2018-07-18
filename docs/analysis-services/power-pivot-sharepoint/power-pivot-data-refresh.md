---
title: Power Pivot 資料重新整理 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2647d94f0f1d8edc1d5c6ef9b364167f330e30a2
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981440"
---
# <a name="power-pivot-data-refresh"></a>Power Pivot 資料重新整理
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  在建立包含 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料的活頁簿之後，您可能會想要定期重新整理資料，其方式是重新執行查詢或命令，以取得您原先用來建立活頁簿之來源的更新資訊。 此處理序稱為 **資料重新整理**，而且您可以在 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]中視需要重新整理資料，或是將其當做已排程的作業，在 SharePoint 伺服器陣列中的應用程式伺服器上，以 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 處理序的方式執行。 如需詳細資訊，請參閱：  
  
-   [Power Pivot 資料重新整理與 SharePoint 2010](http://msdn.microsoft.com/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [設定 Power Pivot 無人看管的資料重新整理帳戶 (Power Pivot for SharePoint)](http://msdn.microsoft.com/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [設定 Power Pivot 資料重新整理 (Power Pivot for SharePoint) 的預存的認證](http://msdn.microsoft.com/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [排程資料重新整理 (Power Pivot for SharePoint)](http://msdn.microsoft.com/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [檢視資料重新整理記錄 &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 和 SharePoint Server 2013 Excel Services 會使用不同的架構進行的資料重新整理[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]資料模型。 SharePoint 2013 支援的架構會運用 Excel Services 作為主要元件來載入 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 資料模型。 先前的資料重新整理架構會使用並仰賴在 SharePoint 模式下執行 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 系統服務和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的伺服器來載入資料模型。 如需詳細資訊，請參閱下列內容：  
>   
>  -   [SharePoint 2013 中的 PowerPivot 資料重新整理](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [升級活頁簿和排程的資料重新整理 &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
