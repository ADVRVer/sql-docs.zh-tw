---
title: "檔案系統工作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.filesystemtask.f1"
helpviewer_keywords: 
  - "檔案系統工作 [Integration Services]"
ms.assetid: 7dd79a6a-e066-4028-a385-1d40f31056f8
caps.latest.revision: 58
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 58
---
# 檔案系統工作
  「檔案系統」工作會在檔案系統中的檔案和目錄上執行作業。 例如，封裝可使用「檔案系統」工作建立、移動或刪除目錄和檔案。 您也可以使用「檔案系統」工作設定檔案和目錄的屬性。 例如，「檔案系統」工作可將檔案設為隱藏或唯讀。  
  
 所有「檔案系統」工作作業均使用來源，其可為檔案或目錄。 例如，工作所複製的檔案或刪除的目錄即為來源。 來源可使用指向目錄或檔案的「檔案」連接管理員指定，或藉由提供包含來源路徑的變數名稱指定。 如需詳細資訊，請參閱[檔案連線管理員](../../integration-services/connection-manager/file-connection-manager.md)和 [Integration Services &#40;SSIS&#41; 變數](../../integration-services/integration-services-ssis-variables.md)。  
  
 複製和移動檔案與目錄以及重新命名檔案的作業會使用目的地和來源。 目的地是使用「檔案」連接管理員或變數指定。 檔案系統工作的作業可設定為允許覆寫目的地檔案和目錄。 建立新目錄的作業可設定為當目錄已存在時使用具有指定名稱的現有目錄，而不會失敗。  
  
## 預先定義的檔案系統作業  
 「檔案系統」工作包括一組預先定義的作業。 下表描述這些作業。  
  
|運算|說明|  
|---------------|-----------------|  
|複製目錄|將資料夾從一個位置複製到另一個。|  
|複製檔案|將檔案從一個位置複製到另一個。|  
|建立目錄|在指定的位置建立資料夾。|  
|刪除目錄|刪除指定位置的資料夾。|  
|刪除目錄內容|刪除某個資料夾中的所有檔案和資料夾。|  
|刪除檔案|刪除指定位置的檔案。|  
|移動目錄|將資料夾從一個位置移到另一個。|  
|移動檔案|將檔案從一個位置移到另一個。|  
|重新命名檔案|重新命名指定位置的檔案。|  
|設定屬性|設定檔案和資料夾的屬性。 屬性包括「封存」、「隱藏」、「一般」「唯讀」和「系統」。 「一般」表示無任何屬性，且不可與其他屬性結合。 其他所有屬性都可互相結合使用。|  
  
 「檔案系統」工作會在單一檔案或目錄上運作。 因此，這項工作不支援使用萬用字元在多個檔案上執行相同的作業。 為了要讓「檔案系統」工作在多個檔案或目錄上重複作業，請將「檔案系統」工作放入 Foreach 迴圈容器內，如以下步驟所述：  
  
-   **設定 Foreach 迴圈容器** ：在 [Foreach 迴圈編輯器] 的 **[集合]** 頁面上，將列舉值設定為 **[Foreach 檔案列舉值]** 然後輸入萬用字元運算式，做為 **[檔案]**的列舉值組態。 在 [Foreach 迴圈編輯器] 的 **[變數對應]** 頁面上，對應您要使用的變數，以便將檔案名稱傳遞到 [檔案系統] 工作，一次一個。  
  
-   **加入和設定檔案系統工作** ：將「檔案系統」工作加入到「Foreach 迴圈」容易。 在「檔案系統工作編輯器」的 **[一般]** 頁面上，將 **[SourceVariable]** 或 **[DestinationVariable]** 屬性設定為您在「Foreach 迴圈」容器中定義的變數。  
  
## 檔案系統工作上可用的自訂記錄項目  
 下表描述「檔案系統」工作的自訂記錄項目。 如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../../integration-services/performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../../integration-services/performance/custom-messages-for-logging.md)。  
  
|記錄項目|說明|  
|---------------|-----------------|  
|**FileSystemOperation**|報告工作執行的作業。 記錄項目會在檔案系統作業開始時寫入，項目中包含有關來源和目的地的資訊。|  
  
## 設定檔案系統工作  
 您可以透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」或以程式設計方式設定屬性。  
  
 如需有關可在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請參閱下列主題：  
  
-   [檔案系統工作編輯器 &#40;一般頁面&#41;](../../integration-services/control-flow/file-system-task-editor-general-page.md)  
  
-   [運算式頁面](../../integration-services/expressions/expressions-page.md)  
  
 如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請參閱下列主題：  
  
-   [設定工作或容器的屬性](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
 如需有關如何以程式設計的方式設定這些屬性的詳細資訊，請參閱下列主題：  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>  
  
## 相關工作  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包括下載和上傳資料檔以及管理伺服器上目錄的工作。 如需相關資訊，請參閱 [FTP Task](../../integration-services/control-flow/ftp-task.md)。  
  
## 請參閱＜  
 [Integration Services 工作](../../integration-services/control-flow/integration-services-tasks.md)   
 [控制流程](../../integration-services/control-flow/control-flow.md)  
  
  