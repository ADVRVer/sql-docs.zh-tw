---
title: 第 6 課： 執行 RDL 結構描述應用程式 (VB-C#) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: a2cd2386-2df8-4b69-ab81-9ad1a31f6d27
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 09d5ad740cb692549d56b9226bc3c7ad5bb234a4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175778"
---
# <a name="lesson-6-run-the-rdl-schema-application-vb-c"></a>第 6 課： 執行 RDL 結構描述應用程式 (VB-C#)
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供兩種從整合式開發環境 (IDE) 建立與執行主控台應用程式的方法：  
  
-   啟動並偵錯  
  
-   啟動但不偵錯  
  
### <a name="to-build-and-run-the-samplerdlschema-application"></a>建立並執行 SampleRDLSchema 應用程式  
  
1.  從**偵錯**功能表上，按一下**啟動但不偵錯**。 這能確保在程式執行完成後，主控台視窗仍維持開啟的狀態。  
  
     應用程式會列印以下的輸出結果到主控台中：  
  
    ```  
    Loading Report Definition  
    Updating Report Definition  
    - Old Description: <Old Report Description>  
    - New Description: <New Report Description>  
    Publishing Report Definition  
    ```  
  
2.  按任意鍵，關閉主控台。  
  
    > [!NOTE]  
    >  發生的任何錯誤都會寫入主控台。  
  
3.  範例應用程式完成執行以後，會將已更新的報表副本儲存至報表伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [使用從 RDL 結構描述產生的類別更新報表&#40;SSRS 教學課程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [報表定義語言 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
