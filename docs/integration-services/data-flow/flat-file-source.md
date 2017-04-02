---
title: "一般檔案來源 | Microsoft Docs"
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
  - "sql13.dts.designer.flatfilesource.f1"
helpviewer_keywords: 
  - "來源 [Integration Services], 一般檔案"
  - "文字檔讀取 [Integration Services]"
  - "一般檔案"
  - "一般檔案來源"
ms.assetid: 4a64f7f3-f25d-4db0-93b3-a29496030e58
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# 一般檔案來源
  「一般檔案」來源會從文字檔讀取資料。 文字檔可以是使用分隔符號、固定寬度或混合的格式。  
  
-   分隔符號格式會使用資料行和資料列分隔符號，來定義資料行和資料列。  
  
-   固定寬度格式會使用寬度來定義資料行和資料列。 此格式亦包含將欄位填補成其最大寬度的字元。  
  
-   不齊右格式會使用寬度來定義所有資料行，最後一個資料行除外，其是以資料列分隔符號所分隔。  
  
 您可以利用下列方式設定「一般檔案」來源：  
  
-   將資料行加入至轉換輸出，該輸出包含「一般檔案」來源從中擷取資料的文字檔檔名。  
  
-   指定「一般檔案」來源是否將資料行中的零長度字串解譯為 Null 值。  
  
    > [!NOTE]  
    >  「一般檔案」來源使用的「一般檔案」連接管理員，必須設定成使用分隔符號格式將零長度字串解譯為 Null。 如果連接管理員使用固定寬度或不齊右格式，則由空格組成的資料就無法解譯為 Null 值。  
  
 一般檔案來源輸出中的輸出資料行包含 FastParse 屬性。 FastParse 可指定資料行要使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 所提供之速度較快，但不區分地區設定的快速剖析常式，或要使用會區分地區設定的標準剖析常式。 如需詳細資訊，請參閱[快速剖析](../Topic/Fast%20Parse.md)和[標準剖析](../Topic/Standard%20Parse.md)。  
  
 輸出資料行也包含 UseBinaryFormat 屬性。 您可使用此屬性在檔案中實作二進位資料的支援，例如具有壓縮之十進位格式的資料。 UseBinaryFormat 預設為 [false]。 如果您想要使用二進位格式，請將 UseBinaryFormat 設為 [true]，並將輸出資料行上的資料類型設為 **DT_BYTES**。 當您執行這個動作時，一般檔案來源會略過資料轉換，並將資料直接傳遞到輸出資料行。 然後您就可以使用「衍生的資料行」或「資料轉換」等轉換，將 **DT_BYTES** 資料轉換成不同的資料類型，或者您可以在「指令碼」轉換中撰寫自訂指令碼來解譯資料。 您也可以撰寫自訂的資料流程元件來解譯資料。 如需您可將 **DT_BYTES** 轉換為何種資料類型的詳細資訊，請參閱[轉換 &#40;SSIS 運算式&#41;](../../integration-services/expressions/cast-ssis-expression.md)。  
  
 此來源使用「一般檔案」連接管理員存取文字檔。 藉由設定「一般檔案」連接管理員上的屬性，即可提供有關該檔案及其中各資料行的資訊，以及指定「一般檔案」來源應如何處理文字檔中的資料。 例如，您可以指定分隔檔案中資料行和資料列的字元，以及各資料行的資料類型和長度。 如需相關資訊，請參閱 [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md)。  
  
 此來源有一個輸出和一個錯誤輸出。  
  
## 設定一般檔案來源  
 您可以透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」或以程式設計方式設定屬性。  
  
 如需有關 **[一般檔案來源編輯器]** 對話方塊中可設定屬性的詳細資訊，請按一下下列其中一個主題：  
  
-   [一般檔案來源編輯器 &#40;連接管理員頁面&#41;](../../integration-services/data-flow/flat-file-source-editor-connection-manager-page.md)  
  
-   [一般檔案來源編輯器 &#40;資料行頁面&#41;](../../integration-services/data-flow/flat-file-source-editor-columns-page.md)  
  
-   [一般檔案來源編輯器 &#40;錯誤輸出頁面&#41;](../../integration-services/data-flow/flat-file-source-editor-error-output-page.md)  
  
 **[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。 如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：  
  
-   [通用屬性](../Topic/Common%20Properties.md)  
  
-   [一般檔案自訂屬性](../../integration-services/data-flow/flat-file-custom-properties.md)  
  
## 相關工作  
 如需如何設定資料流程元件屬性的詳細資訊，請參閱[設定資料流程元件的屬性](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)。  
  
## 請參閱＜  
 [一般檔案目的地](../../integration-services/data-flow/flat-file-destination.md)   
 [資料流程](../../integration-services/data-flow/data-flow.md)  
  
  