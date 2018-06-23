---
title: 建立基本資料表報表 (SSRS 教學課程) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
caps.latest.revision: 61
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 4f8b3f60d82a94fa7289054d0028ab539abade64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36037412"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a>建立基本資料表報表 (SSRS 教學課程)
  本教學課程設計來協助您建立基本資料表報表根據[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]資料庫使用報表設計師。 您也可以使用報表產生器或報表精靈來建立報表。 在這個教學課程中，您將建立報表專案、設定連接資訊、定義查詢、加入資料表資料區域、群組與加總某些欄位，以及預覽報表。  
  
> [!NOTE]  
>  為了完成這個教學課程，[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 必須以原生模式執行。 如果 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 是在 SharePoint 整合模式中執行，則所有用到報表伺服器 URL 的步驟都將無法運作。 如需有關[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]模式，請參閱[Reporting Services 報表伺服器](reporting-services-report-server.md)。  
  
## <a name="requirements"></a>需求  
 您的系統必須已經安裝下列項目，才能使用這個教學課程：  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 資料庫引擎。  
  
-   [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫。  如需詳細資訊，請參閱[Adventure Works for SQL Server 2012 (Adventure Works for SQL Server 2012)](http://go.microsoft.com/fwlink/?LinkId=245471) (http://go.microsoft.com/fwlink/?LinkId=245471).。 如需有關支援[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]範例資料庫和範例程式碼[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]，請參閱[資料庫及範例概觀](http://go.microsoft.com/fwlink/?LinkId=110391)CodePlex 網站上。  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 您也必須擁有要從中擷取資料的唯讀權限[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]資料庫。  
  
## <a name="tasks"></a>工作  
 [第 1 課： 建立報表伺服器專案&#40;Reporting Services&#41;](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [第 2 課： 指定連接資訊&#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [第 3 課： 定義資料表報表的資料集&#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [第 4 課： 將資料表加入至報表&#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [第 5 課： 格式化報表&#40;Reporting Services&#41;](lesson-5-formatting-a-report-reporting-services.md)  
  
 [第 6 課： 加入群組和總計&#40;Reporting Services&#41;](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  當檢閱教學課程，我們建議您將加入**下一步**和**上一步**文件檢視器工具列的按鈕。 如需詳細資訊，請參閱。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 教學課程 &#40;SSRS&#41;](reporting-services-tutorials-ssrs.md)  
  
  