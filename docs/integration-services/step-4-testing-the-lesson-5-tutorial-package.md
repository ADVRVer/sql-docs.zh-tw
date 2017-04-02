---
title: "步驟 4：測試第 5 課的教學課程封裝 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# 步驟 4：測試第 5 課的教學課程封裝
在執行階段，您的封裝將從執行階段更新的變數中取得 **Directory** 屬性的值，而不是使用您建立封裝時指定的原始目錄名稱。 變數的值會由 SSISTutorial.dtsConfig 檔案擴展。  
  
若要確認封裝在執行階段使用新值來更新 Directory 屬性，只要執行封裝即可。 因為只有 3 個範例資料檔會複製到新目錄，所以資料流程只會執行 3 次，而不是反覆執行原始資料夾的 14 個檔案。  
  
## 檢查封裝配置  
在測試封裝之前，您應該確認第 5 課封裝中的控制流程和資料流程是否包含下圖所顯示的物件。 其控制流程應該與第 4 課的控制流程相同。 資料流程應該與第 4 課的資料流程完全相同。  
  
**控制流程**  
  
![Control flow in package](../integration-services/media/task4lesson2control.gif "Control flow in package")  
  
**資料流程**  
  
![Data flow in package](../integration-services/media/task9lesson1data.gif "Data flow in package")  
  
### 若要測試第 5 課的教學課程封裝  
  
1.  在 **[偵錯]** 功能表上，按一下 **[開始偵錯]**。  
  
2.  在封裝完成執行之後，在 **[偵錯]** 功能表上，按一下 **[停止偵錯]**。  
  
## 下一課  
[第 6 課：在 SSIS 中搭配專案部署模型使用參數](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
  
