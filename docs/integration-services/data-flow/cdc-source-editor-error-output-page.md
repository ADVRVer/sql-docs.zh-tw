---
title: "CDC 來源編輯器 (錯誤輸出頁面) | Microsoft Docs"
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
  - "sql13.ssis.designer.cdcsource.errorhandling.f1"
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# CDC 來源編輯器 (錯誤輸出頁面)
  使用 [CDC 來源編輯器] 對話方塊的 [錯誤輸出] 頁面，即可選取錯誤處理選項。  
  
 若要了解有關 CDC 來源的詳細資訊，請參閱＜ [CDC Source](../../integration-services/data-flow/cdc-source.md)＞。  
  
## 工作清單  
 **若要開啟 CDC 來源編輯器的錯誤輸出頁面**  
  
1.  在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，開啟具有 CDC 來源的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 封裝。  
  
2.  在 [資料流程] 索引標籤中，按兩下 CDC 來源。  
  
3.  在 [CDC 來源編輯器] 中，按一下 [錯誤輸出]。  
  
## 選項。  
 **輸入/輸出**  
 檢視資料來源的名稱。  
  
 **資料行**  
 檢視您在 [CDC 來源編輯器] 對話方塊的 [連線管理員] 頁面上所選取的外部 (來源) 資料行。  
  
 **錯誤**  
 選取 CDC 來源應該如何處理流程中的錯誤：忽略失敗、重新導向資料列，或使元件失效。  
  
 **截斷**  
 選取 CDC 來源應該如何處理流程中的截斷：忽略失敗、重新導向資料列，或使元件失效。  
  
 **說明**  
 未使用。  
  
 **將這個值設定到選取的資料格**  
 選取發生錯誤或截斷時 CDC 來源如何處理所有選取的資料格：忽略失敗、重新導向資料列，或使元件失效。  
  
 **套用**  
 將錯誤處理選項套用至選取的資料格。  
  
## 錯誤處理選項  
 您可以使用下列選項來設定 CDC 來源處理錯誤和截斷的方式。  
  
 **失敗元件**  
 當發生錯誤或截斷時，資料流程工作將失敗。 這是預設行為。  
  
 **忽略失敗**  
 系統會忽略錯誤或截斷，並將資料列導向至 CDC 來源輸出。  
  
 **重新導向流程**  
 系統會將錯誤或截斷資料列導向至 CDC 來源的錯誤輸出。 在此情況中，就會使用 CDC 來源錯誤處理。 如需詳細資訊，請參閱 [CDC 來源](../../integration-services/data-flow/cdc-source.md)。  
  
## 請參閱＜  
 [CDC 來源編輯器 &#40;連線管理員頁面&#41;](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md)   
 [CDC 來源編輯器 &#40;資料行頁面&#41;](../../integration-services/data-flow/cdc-source-editor-columns-page.md)  
  
  