---
title: "開發自訂記錄提供者 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9d5dee6649539d340fd9954798db913136553aae
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-custom-log-provider"></a>開發自訂記錄提供者
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 具有多種記錄功能，可以擷取在封裝執行期間所發生的事件。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包括各種記錄提供者，讓記錄可以 XML、文字、資料庫或 Windows 事件記錄檔格式加以建立並儲存記錄檔。 如果所提供的記錄提供者與輸出格式並未完全符合您的需求，可以建立自訂記錄提供者。  
  
 若要建立自訂記錄提供者，您必須建立繼承自 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基底類別的類別、將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 屬性 (Attribute) 套用至新類別，以及覆寫基底類別的重要方法與屬性 (Property)，包括 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 屬性 (Property) 與 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 方法。  
  
## <a name="in-this-section"></a>섹션 내용  
 本節描述如何建立、設定和撰寫自訂記錄提供者的程式碼。  
  
 [建立自訂記錄提供者](../../../integration-services/extending-packages-custom-objects/log-provider/creating-a-custom-log-provider.md)  
 描述如何為自訂記錄提供者專案建立類別。  
  
 [程式碼撰寫的自訂記錄提供者](../../../integration-services/extending-packages-custom-objects/log-provider/coding-a-custom-log-provider.md)  
 描述如何透過覆寫基底類別的方法與屬性，來實作自訂記錄提供者。  
  
 [開發自訂記錄提供者的使用者介面](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-user-interface-for-a-custom-log-provider.md)  
 自訂記錄提供者的自訂使用者介面中不支援[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]。  
  
## <a name="related-topics"></a>相關主題  
  
### <a name="information-common-to-all-custom-objects"></a>自訂物件的共通資訊  
 如需有關 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之所有類型自訂物件適用的共通資訊，請參閱下列主題：  
  
 [開發 Integration Services 的自訂物件](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 描述為 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 實作所有類型的自訂物件之基本步驟。  
  
 [保存自訂物件](../../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 描述自訂的持續性並解釋必須實作它的時機。  
  
 [自訂物件的建立、部署和偵錯](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 描述建立、簽署、部署和偵錯自訂物件的技術。  
  
### <a name="information-about-other-custom-objects"></a>其他自訂物件的相關資訊  
 如需有關在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之其他類型自訂物件的詳細資訊，請參閱下列主題：  
  
 [開發自訂工作](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)  
 討論如何進行自訂工作的程式設計。  
  
 [開發自訂連接管理員](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 討論如何進行自訂連接管理員的程式設計。  
  
 [開發自訂 ForEach 列舉值](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 討論如何進行自訂列舉值的程式設計。  
  
 [開發自訂資料流程元件](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)  
 討論如何進行自訂資料流程來源、轉換和目的地的程式設計。  
  

