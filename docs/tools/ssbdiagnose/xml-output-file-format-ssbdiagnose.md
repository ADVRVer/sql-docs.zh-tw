---
title: "XML 輸出檔格式 (ssbdiagnose) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML 輸出檔格式 [ssbdiagnose]"
  - "ssbdiagnose"
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# XML 輸出檔格式 (ssbdiagnose)
  當您執行 **ssbdiagnose** 公用程式搭配 **-XML** 參數時，此公用程式就會將其輸出傳遞成 XML 檔。 其 XML 輸出檔會列出標頭資訊以及它在分析之 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 組態或交談中找到的錯誤。 您可以撰寫應用程式來分析或報告該檔案中所列的錯誤。 或者，您可以在一般 XML 編輯器 (例如 XML Notepad) 中檢視此 XML 檔。  
  
 **ssbdiangose** 輸出檔包含具有兩種子類型的 DiagnosticInformation 根元素：  
  
-   具有標頭資訊的 Banner 元素。  
  
-   **ssbdiagnose**所報告之每個問題的 Issue 元素。  
  
## DiagnosticInformation 根元素  
  
-   [DiagnosticInformation 元素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## Banner 元素  
  
-   [Banner 元素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## Issue 元素  
  
-   [Issue 元素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## 另請參閱  
 [ssbdiagnose 公用程式 &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  