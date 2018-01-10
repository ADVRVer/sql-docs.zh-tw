---
title: "開發 Integration Services 的自訂物件 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- custom user interface [Integration Services]
- custom objects [Integration Services]
ms.assetid: ca1929a6-0ae6-47d7-b65f-08173b143720
caps.latest.revision: "31"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 15c30b516ec8d2b19d0f54fb47281c74f7442ec0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="developing-custom-objects-for-integration-services"></a>開發 Integration Services 的自訂物件
  當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 隨附的控制流程與資料流程物件無法完全滿足您的需求時，您可以自行開發許多類型的自訂物件，包括：  
  
-   **自訂工作**。  
  
-   **自訂連線管理員：** 連線至目前不支援的外部資料來源。  
  
-   **自訂記錄提供者：** 使用目前不支援的格式來記錄套件事件。  
  
-   **自訂列舉程式：** 支援反覆運算一組目前不支援其格式的物件或值。  
  
-   **自訂資料流程元件：** 可以設定為來源、轉換或目的地。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 物件模型使用基底類別來協助此自訂開發，這些基底類別可為您的自訂實作提供一致且可靠的架構。  
  
 如果您不必在多個封裝之間重複使用自訂功能，指令碼工作與指令碼元件提供 Managed 程式語言的完整功能，可大幅減少要撰寫的基礎結構程式碼。 如需詳細資訊，請參閱[比較指令碼解決方案和自訂物件](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)。  
  
## <a name="steps-in-developing-a-custom-object-for-integration-services"></a>開發 Integration Services 自訂物件的步驟  
 當您開發要用於 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的自訂物件時，所開發的類別庫 (DLL) 將在設計階段與執行階段由 SSIS 設計師及 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 執行階段載入。 您必須實作的最重要方法，不是從自己的程式碼呼叫的方法，而是執行階段在適當時間呼叫以初始化並驗證您的元件且叫用其功能的方法。  
  
 以下是開發自訂物件所遵循的步驟：  
  
1.  以您慣用的 Managed 程式語言建立「類別庫」類型的新專案。  
  
2.  繼承自適當的基底類別，如下表所示。  
  
3.  將適當的屬性套用至新類別，如下表所示。  
  
4.  視需要覆寫基底類別的方法，並為物件的自訂功能撰寫程式碼。  
  
5.  選擇性地為您的元件建立自訂使用者介面。 為了便於部署，您可能會想要以相同方案中的獨立專案開發使用者介面，並將它建立成個別的組件。  
  
6.  選擇性地在 [SSIS 工具箱] 中顯示範例和自訂物件說明內容的連結。  
  
7.  依[建置、部署和偵錯自訂物件](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)中所述，建置與部署新的自訂物件，並進行偵錯。  
  
## <a name="base-classes-attributes-and-important-methods"></a>基底類別、屬性和重要的方法  
 這個資料表針對您可以開發的各種類型自訂物件，提供 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 物件模型中最重要元素的便利參考。  
  
|自訂物件|基底類別|attribute|重要的方法|  
|-------------------|----------------|---------------|-----------------------|  
|工作|<xref:Microsoft.SqlServer.Dts.Runtime.Task>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>|  
|[ODBC 來源編輯器]|<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A>|  
|記錄提供者|<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>、 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>、 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>|  
|列舉值|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>|  
|資料流程元件|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>|<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>|  
  
## <a name="providing-links-to-samples-and-help-content"></a>提供範例和說明內容的連結  
 若要在 [SSIS 工具箱] 中顯示範例和自訂物件 (以受控碼撰寫) 的說明內容連結，請使用下列屬性。  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.SamplesTag%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.HelpCollection%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.HelpKeyword%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.SamplesTag%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.HelpCollection%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.HelpKeyword%2A>  
  
 若要顯示範例和以機器碼撰寫之自訂物件說明內容的連結，請在 SamplesTag、HelpKeyword 和 HelpCollection 的登錄指令碼 (.rgs) 檔案中加入項目。 以下是一個範例。  
  
 `val HelpKeyword = s 'sql11.dts.designer.executepackagetask.F1'`  
  
 `val SamplesTag = s 'ExecutePackageTask'`  
  
## <a name="providing-a-custom-user-interface"></a>提供自訂使用者介面  
 若要允許自訂物件的使用者設定其屬性，您可能也必須開發自訂使用者介面。 在並非絕對需要自訂使用者介面的情況下，您可以選擇建立一個介面以提供比預設編輯器更好用的介面。  
  
 在自訂使用者介面專案或是組件中，通常有兩個類別：針對特定類型的自訂物件之使用者介面實作 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 介面的類別，以及它所顯示的 Windows Form，以蒐集使用者資訊。 您實作的介面只有一些方法，而且自訂使用者介面並不難開發。  
  
> [!NOTE]  
>  許多 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 記錄提供者都有自訂使用者介面，以實作 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>，並將 [設定] 文字方塊取代為可用的連線管理員篩選下拉式清單。 不過，在這個版本的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中並未實作自訂記錄提供者的自訂使用者介面。 指定 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 屬性值將沒有任何作用。  
  
 下表提供您在為每個類型的自訂物件開發自訂使用者介面時，必須實作的介面之便利參考。 它也說明在下列情況下使用者會看到的內容：當您選擇不要為物件開發自訂使用者介面，或當您無法使用物件屬性 (Attribute) 中的 **UITypeName** 屬性 (Property) 將物件連結到其使用者介面時。 雖然強大的 [進階編輯器] 可能可以滿足資料流程元件，不過，[屬性] 視窗對於工作與連接管理員而言較缺乏使用者親和性，而且如果沒有自訂表單，根本無法設定自訂 ForEach 列舉值。  
  
|自訂物件|使用者介面的基底類別|沒有提供自訂使用者介面時的預設編輯行為|  
|-------------------|-----------------------------------|----------------------------------------------------------------------|  
|工作|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>|僅 [屬性] 視窗|  
|[ODBC 來源編輯器]|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>|僅 [屬性] 視窗|  
|記錄提供者|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI><br /><br /> (尚未在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中實作)|[設定] 資料行中的文字方塊|  
|列舉值|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>|僅 [屬性] 視窗。 編輯器的 [列舉值組態] 區域是空的。|  
|資料流程元件|<xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI>|進階編輯器|  
  
## <a name="external-resources"></a>外部資源  
  
-   blogs.msdn.com 上的部落格文章 [Visual Studio solution build process give a warning about indirect dependency on the .NET Framework assembly due to SSIS references](http://go.microsoft.com/fwlink/?LinkId=215662) (Visual Studio 方案建置程序提出了因為 SSIS 參考而與 .NET Framework 組件之間有間接相依性的警告 )。  
  
## <a name="see-also"></a>另請參閱  
 [保存自訂物件](../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)   
 [自訂物件的建立、部署和偵錯](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
  
  
