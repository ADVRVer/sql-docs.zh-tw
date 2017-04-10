---
title: "第 3 課︰使用 SSIS 新增記錄功能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# 第 3 課︰使用 SSIS 新增記錄功能
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供工作和容器事件的追蹤，包含可讓您進行疑難排解及監視套件執行的記錄功能。 記錄功能很有彈性，可在封裝層級或在封裝內的個別工作和容器上啟用。 您可以選取要記錄的事件，以及針對單一封裝建立多個記錄。  
  
記錄是由記錄提供者提供。 每一個記錄提供者都可將記錄資訊寫入至不同格式和目的地類型。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供下列記錄提供者：  
  
-   文字檔  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Windows 事件記錄檔  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML 檔  
  
在這一課，您將建立在[第 2 課：使用 SSIS 新增迴圈](../integration-services/lesson-2-adding-looping-with-ssis.md)所建立的套件複本。 利用這個新的封裝，您可以加入和設定記錄，在封裝執行期間監視特定事件。 如果您尚未完成前面任何一課，您也可以複製此教學課程所包含之已完成的第 2 課封裝。  
  
> [!IMPORTANT]  
> 這個教學課程需要 **AdventureWorksDW2012** 範例資料庫。 如需如何安裝和部署 **AdventureWorksDW2012** 的詳細資訊，請參閱 [Reporting Services Product Samples on CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910) (CodePlex 上的 Reporting Services 產品範例)  
  
## 課程工作  
這一課包含下列工作：  
  
-   [步驟 1：複製第 2 課的套件](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
-   [步驟 2：加入和設定記錄](../integration-services/step-2-adding-and-configuring-logging.md)  
  
-   [步驟 3：測試第 3 課的教學課程封裝](../integration-services/step-3-testing-the-lesson-3-tutorial-package.md)  
  
## 開始課程  
[步驟 1：複製第 2 課的套件](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
  
  
