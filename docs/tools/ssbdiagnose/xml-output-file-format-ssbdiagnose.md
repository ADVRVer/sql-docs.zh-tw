---
title: XML 輸出檔案格式
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 50d1c8467c3ec7d51325b1a2beaad8f9216f0dbc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254176"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>XML 輸出檔格式 (ssbdiagnose)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

當您執行 **ssbdiagnose** 公用程式搭配 **-XML** 參數時，此公用程式就會將其輸出傳遞成 XML 檔。 其 XML 輸出檔會列出標頭資訊以及它在分析之 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 組態或交談中找到的錯誤。 您可以撰寫應用程式來分析或報告該檔案中所列的錯誤。 或者，您可以在一般 XML 編輯器 (例如 XML Notepad) 中檢視此 XML 檔。  
  
 **ssbdiangose** 輸出檔包含具有兩種子類型的 DiagnosticInformation 根元素：  
  
-   具有標頭資訊的 Banner 元素。  
  
-   **ssbdiagnose**所報告之每個問題的 Issue 元素。  
  
## <a name="diagnosticinformation-root-element"></a>DiagnosticInformation 根元素  
  
-   [DiagnosticInformation 元素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Banner 元素  
  
-   [Banner 元素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Issue 元素  
  
-   [Issue 元素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>另請參閱  
 [ssbdiagnose 公用程式 &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
