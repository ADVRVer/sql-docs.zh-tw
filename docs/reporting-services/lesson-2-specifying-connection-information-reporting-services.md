---
title: "第 2 課： 指定連接資訊 (Reporting Services) |Microsoft 文件"
ms.custom: 
ms.date: 05/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 53
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4d0667dec1b59d5560ca24176634dddc5d6d8d18
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>第 2 課：指定連接資訊 (Reporting Services)
您將加入之後[!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)]分頁至您在第 1 課的教學課程專案的報表，您現在必須定義*資料來源*，這是報表用來存取資料從關聯式資料庫、 多維度資料庫或另一個來源的連接資訊。  
  
在這一課，您可以使用[!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]範例資料庫做為資料來源。 本教學課程假設這個資料庫位於預設執行個體[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)]安裝在本機電腦上。  
  
### <a name="to-set-up-a-connection"></a>設定連接  
  
1.  在**報表資料** 窗格中，按一下 **新增**，然後按一下 **資料來源**。  
如果看不到 [報表資料] 窗格，請按一下 [檢視] 功能表上的 [報表資料]。  

    ![ssrs-table-tutorial-2-new-data-source](../reporting-services/media/ssrs-table-tutorial-2-new-data-source.png)
  
   2.  在**名稱**，型別*AdventureWorks2014*。  
  
3.  確認 [內嵌連接] 已選取。  
  
4.  在 [類型] 中，選取 [Microsoft SQL Server]。  
  
5.  在 [連接字串] 中，輸入下列字串：  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
     這個連接字串假設 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、報表伺服器和 [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] 資料庫都安裝在本機電腦上，且您有登入 [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] 資料庫的權限。 如果 AdventureWorks2014 資料庫不是本機電腦上，變更連接字串，並取代*localhost*資料庫的伺服器執行個體的名稱。
  
     >[!NOTE]  
    >如果您使用 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services 或具名執行個體，則連接字串必須包括執行個體資訊：  
    >  
    >`Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
    >  
    >如需連接字串的詳細資訊，請參閱： [Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)。  
     
  
6.  按一下左窗格中的 [認證]，然後按一下 [使用 Windows 驗證 (整合式安全性)]。  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]資料來源**AdventureWorks2014**加入至**報表資料**窗格。  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## <a name="next-task"></a>下一項工作  
您已順利定義 [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] 範例資料庫的連接。 下一步，您將建立報表。 請參閱[第 3 課：定義資料表報表的資料集 &#40;Reporting Services&#41;](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)。  
  
## <a name="see-also"></a>另請參閱  
[Data Connections, Data Sources, and Connection Strings in Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  


