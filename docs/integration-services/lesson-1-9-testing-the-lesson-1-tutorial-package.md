---
title: "步驟 9： 測試第 1 課的教學課程封裝 |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ca45e8e1ba02246eb5429bd7bfea125663f69f41
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-1-9---testing-the-lesson-1-tutorial-package"></a>課程 1-9： 測試第 1 課的教學課程封裝
在這一課，您完成了下列工作：  
  
-   建立新的 [!INCLUDE[ssIS](../includes/ssis-md.md)] 專案。  
  
-   設定封裝要連接到來源和目的地資料時所需的連接管理員。  
  
-   加入資料流程來取得一般檔案來源的資料，對資料執行必要的查閱轉換，以及設定目的地的資料。  
  
現在已完成封裝！ 測試封裝的時間到了。  
  
## <a name="checking-the-package-layout"></a>檢查封裝配置  
在測試封裝之前，您應該確認第 1 課封裝中的控制流程和資料流程是否包含下圖所顯示的物件。  
  
**控制流程**  
  
![控制流程封裝中](../integration-services/media/task9lesson1control.gif "控制流程封裝中")  
  
**資料流程**  
  
![封裝中的資料流程](../integration-services/media/task9lesson1data.gif "中封裝的資料流程")  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a>若要執行第 1 課的教學課程封裝  
  
1.  在 **[偵錯]** 功能表上，按一下 **[開始偵錯]**。  
  
    封裝隨即執行，讓 1097 個資料列順利加入 **AdventureWorksDW2012** 的 **FactCurrency**事實資料表中。  
  
2.  在封裝完成執行之後，在 **[偵錯]** 功能表上，按一下 **[停止偵錯]**。  
  
## <a name="next-lesson"></a>下一課  
[第 2 課：使用 SSIS 新增迴圈](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a>另請參閱  
[執行專案和封裝](https://msdn.microsoft.com/library/ms141708(v=sql.110).aspx) 
  
  
  

