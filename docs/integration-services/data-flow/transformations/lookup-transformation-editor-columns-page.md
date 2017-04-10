---
title: "查閱轉換編輯器 (資料行頁面) | Microsoft Docs"
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
  - "sql13.dts.designer.lookuptransformation.columns.f1"
helpviewer_keywords: 
  - "查閱轉換編輯器"
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 39
---
# 查閱轉換編輯器 (資料行頁面)
  使用 **[查閱轉換編輯器]** 對話方塊的 **[資料行]** 頁面，即可指定來源資料表和參考資料表之間的聯結，以及從參考資料表中選取查閱資料行。  
  
 若要深入了解查閱轉換，請參閱＜ [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md)＞。  
  
## 選項。  
 **可用的輸入資料行**  
 檢視可用的輸入資料行清單。 輸入資料行是連接來源的資料流程中的資料行。 輸入資料行和查閱資料行必須有相符的資料類型。  
  
 使用拖放作業，即可將可用的輸入資料行對應到查閱資料行。  
  
 您也可以藉由在 **[可用的輸入資料行]** 資料表中反白顯示資料行，按下應用程式鍵，然後按一下 **[編輯對應]**，使用鍵盤將輸入資料行對應到查閱資料行。  
  
 **可用的查閱資料行**  
 檢視查閱資料行清單。 查閱資料行是參考資料表中的資料行，您可在其中查閱符合輸入資料行的值。  
  
 使用拖放作業，即可將可用的查閱資料行對應到輸入資料行。  
  
 使用核取方塊即可在參考資料表中，選取要執行查閱作業的查閱資料行。  
  
 您也可以藉由在 **[可用的查閱資料行]** 資料表中反白顯示資料行，按下應用程式鍵，然後按一下 **[編輯對應]**，使用鍵盤將查閱資料行對應到輸入資料行。  
  
 **查閱資料行**  
 檢視選取的查閱資料行。 您的選擇會反映在 **[可用的查閱資料行]** 資料表的核取方塊選擇中。  
  
 **查閱作業**  
 從清單中選取要在查閱資料行上執行的查閱作業。  
  
 **輸出別名**  
 輸入每個查閱資料行之輸出的別名。 預設是查閱資料行的名稱；但是，您可以選取任何唯一的描述性名稱。  
  
## 請參閱＜  
 [查閱轉換編輯器 &#40;一般頁面&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-general-page.md)   
 [查閱轉換編輯器 &#40;連接頁面&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-connection-page.md)   
 [查閱轉換編輯器 &#40;進階頁面&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-advanced-page.md)   
 [查閱轉換編輯器 &#40;錯誤輸出頁面&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-error-output-page.md)   
 [模糊查閱轉換](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  