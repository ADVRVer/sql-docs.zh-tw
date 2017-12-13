---
title: "第 8 課： 定義動作 |Microsoft 文件"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 605c4ae52c6e6f51ff03eb5ff161603b9fb082e9
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-8-defining-actions"></a>第 8 課：定義動作
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]在這一課，您將學會定義中的動作程式[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]專案。 動作只是一個儲存在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的多維度運算式 (MDX) 陳述式，可以併入用戶端應用程式中，由使用者啟動。  
  
> [!NOTE]  
> 此教學課程中，所有課程已完成的專案都可在線上取得。 您可以從先前的課程中使用已完成的專案做為起點，向前跳到任何課程。 [按一下這裡](http://go.microsoft.com/fwlink/?LinkID=221866) ，下載此教學課程隨附的範例專案。  
  
[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支援下表所說明的動作類型。  
  
|||  
|-|-|  
|CommandLine|在命令提示字元執行命令。|  
|資料集|將資料集傳回用戶端應用程式。|  
|鑽研|將 drillthrough 陳述式當做運算式傳回，用戶端會執行這個運算式來傳回資料列集。|  
|HTML|在網際網路瀏覽器中執行 HTML 指令碼。|  
|專屬|使用不同於此資料表列出的介面來執行作業。|  
|報表|將一個以 URL 為基礎的參數化要求，提交給報表伺服器，然後將報表傳回用戶端應用程式。|  
|資料列集|將資料列集傳回用戶端應用程式。|  
|Statement|執行 OLE DB 命令。|  
|URL|在網際網路瀏覽器中顯示動態網頁。|  
  
動作可讓使用者啟動應用程式，或者在所選項目的內容當中執行其他步驟。 如需詳細資訊，請參閱 [動作 &#40;Analysis Services - 多維度資料&#41;](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)和 [多維度模型中的動作](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)  
  
> [!NOTE]  
> 若要取得動作的範例，請參閱 [計算工具] 窗格中 [範本] 索引標籤上的動作範例，或是 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 範例資料倉儲中的範例。 如需此資料庫的安裝詳細資訊，請參閱 [安裝 Analysis Services 多維度模型化教學課程的範例資料和專案](../analysis-services/install-sample-data-and-projects.md)。  
  
這一課包含下列工作：  
  
[定義和使用鑽研動作](../analysis-services/lesson-8-1-defining-and-using-a-drillthrough-action.md)  
在這項工作中，您要透過稍早在教學課程中所定義的事實維度關聯性，來定義、使用，然後修改鑽研動作。  
  
## <a name="next-lesson"></a>下一課  
[第 9 課：定義檢視方塊和翻譯](../analysis-services/lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>另請參閱  
[Analysis Services 教學課程案例](../analysis-services/analysis-services-tutorial-scenario.md)  
[多維度模型化 &#40;Adventure Works 教學課程&#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[動作 &#40;Analysis Services - 多維度資料&#41;](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)  
[多維度模型中的動作](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)  
  
  
  
