---
title: "偵錯資料處理延伸模組程式碼 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
caps.latest.revision: "40"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6a21ea00e93516c6e6fd60e3102c618674a4304d
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="debugging-data-processing-extension-code"></a>偵錯資料處理延伸模組程式碼
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供數個偵錯工具，可協助您分析資料處理延伸模組程式碼，並尋找其中的錯誤。 效果最好的工具將視您嘗試要完成的項目而定。 此範例會使用 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]。  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>偵錯資料處理延伸模組程式碼  
  
1.  啟動 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]，並開啟您的資料處理延伸模組專案。  
  
2.  建立專案，然後將資料處理延伸模組組件與隨附的 .pdb 檔案，部署到報表設計師。 如需部署的詳細資訊，請參閱[如何：將資料處理延伸模組部署到報表設計師](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md)。  
  
3.  在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中開啟新的 [報表專案]，同時在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的個別視窗中，將資料處理延伸模組程式碼保持在開啟的狀態。  
  
4.  導覽到包含資料處理延伸模組專案的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 視窗，並在程式碼中設定某些中斷點。  
  
5.  當資料處理延伸模組專案視窗仍為使用中時，按一下 [偵錯] 功能表的 [附加至處理序]。  
  
     [附加至處理序] 對話方塊隨即開啟。  
  
6.  從處理序清單中，選取對應至報表專案的 devenv.exe 處理序，然後按一下 [附加]。  
  
7.  您可以使用報表專案的 [報表資料] 索引標籤來定義報表資料來源。 您最有可能使用一般查詢設計工具，以針對自訂資料來源來執行查詢。 這應該會叫用偵錯工具並執行對應至中斷點的程式碼。  
  
8.  使用 F11 鍵逐步執行程式碼。 如需有關使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 進行偵錯的詳細資訊，請參閱您的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文件集。  
  
## <a name="see-also"></a>另請參閱  
 [部署資料處理延伸模組](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Reporting Services 延伸模組](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [實作資料處理延伸模組](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 延伸模組程式庫](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
