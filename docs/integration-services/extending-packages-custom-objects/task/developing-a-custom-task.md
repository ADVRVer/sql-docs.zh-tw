---
title: "開發自訂工作 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom tasks [Integration Services], about custom tasks
- Task class
- custom tasks [Integration Services]
- SSIS custom tasks
- SSIS custom tasks, about custom tasks
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- tasks [Integration Services], custom
- TaskHost object
ms.assetid: dcbd8615-fa6d-4ddb-b8a5-0b19dddd6239
caps.latest.revision: 67
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a6f9c16453365ce5b7a278f352c8cec8d86c2780
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-custom-task"></a>開發自訂工作
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 利用工作執行工作單位，以支援擷取、轉換及載入資料。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包含各種可以執行最常使用之動作的工作，包括執行 SQL 陳述式、從 FTP 站台下載檔案等。 如果包含的工作與支援的動作未完全符合您的需求，可以建立自訂工作。  
  
 若要建立自訂工作，您必須建立繼承自 <xref:Microsoft.SqlServer.Dts.Runtime.Task> 基底類別的類別、將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 屬性 (Attribute) 套用至新類別，以及覆寫基底類別的重要方法與屬性 (Property)，包括 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法。  
  
## <a name="in-this-section"></a>本節內容  
 本章節描述如何建立和設定自訂工作及其選用自訂使用者介面，以及如何撰寫它們的程式碼。  
  
 [建立自訂工作](../../../integration-services/extending-packages-custom-objects/task/creating-a-custom-task.md)  
 描述第一個步驟：建立自訂工作。  
  
 [編寫自訂工作](../../../integration-services/extending-packages-custom-objects/task/coding-a-custom-task.md)  
 描述如何撰寫自訂工作之主要方法的程式碼。  
  
 [連接到自訂工作中的資料來源](../../../integration-services/extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
 描述如何將自訂工作連接到資料來源。  
  
 [引發和自訂工作中定義事件](../../../integration-services/extending-packages-custom-objects/task/raising-and-defining-events-in-a-custom-task.md)  
 描述如何引發事件並從自訂工作定義自訂事件。  
  
 [新增支援自訂工作中的偵錯](../../../integration-services/extending-packages-custom-objects/task/adding-support-for-debugging-in-a-custom-task.md)  
 描述如何在自訂工作中建立中斷點目標。  
  
 [自訂工作開發使用者介面](../../../integration-services/extending-packages-custom-objects/task/developing-a-user-interface-for-a-custom-task.md)  
 描述如何建立顯示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中的使用者介面，以便在自訂工作上設定屬性。  
  
## <a name="related-sections"></a>相關章節  
  
### <a name="information-common-to-all-custom-objects"></a>自訂物件的共通資訊  
 如需有關 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之所有類型自訂物件適用的共通資訊，請參閱下列主題：  
  
 [開發 Integration Services 的自訂物件](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 描述為 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 實作所有種類的自訂物件之基本步驟。  
  
 [保存自訂物件](../../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 描述自訂的持續性並解釋必須實作它的時機。  
  
 [自訂物件的建立、部署和偵錯](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 描述建立、簽署、部署和偵錯自訂物件的技術。  
  
### <a name="information-about-other-custom-objects"></a>其他自訂物件的相關資訊  
 如需有關在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之其他類型自訂物件的詳細資訊，請參閱下列主題：  
  
 [開發自訂連接管理員](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 討論如何進行自訂連接管理員的程式設計。  
  
 [開發自訂記錄提供者](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 討論如何進行自訂記錄提供者的程式設計。  
  
 [開發自訂 ForEach 列舉值](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 討論如何進行自訂列舉值的程式設計。  
  
 [開發自訂資料流程元件](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)  
 討論如何進行自訂資料流程來源、轉換和目的地的程式設計。  
  
## <a name="see-also"></a>另請參閱  
 [Extending the Package with the Script Task](../../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md)   
 [比較指令碼方案和自訂物件](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
