---
title: "Synchronize 命令 (TMSL) |Microsoft 文件"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a32ff053-f38f-49d7-afdc-e19f59c88135
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ef443652815654b5290d9a39c090cef3af4f1f04
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="synchronize-command-tmsl"></a>Synchronize 命令 (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later](../../includes/ssas-appliesto-sql2016-later.md)]

  同步處理 Analysis Services 資料庫與另一個現有的資料庫。  
  
## <a name="request"></a>要求  
 接受的 JSON 屬性同步處理的命令如下。  
  
```  
{   
   "synchronize":{   
      "database":"AdventureWorksDW_Production",  
      "source":"Provider=MSOLAP.7;Data Source=localhost;Integrated Security=SSPI;Initial Catalog=AdventureWorksDW_Dev",  
      "synchronizeSecurity":"copyAll",  
      "applyCompression":true  
   }  
}  
```  
  
 接受的 JSON 屬性同步處理的命令如下。  
  
||||  
|-|-|-|  
|**屬性**|**預設值**|**說明**|  
|[資料庫]||同步處理資料庫物件的名稱。|  
|來源||用來連接到來源伺服器的連接字串。|  
|synchronizeSecurity|skipMembership|列舉值，指定如何還原安全性定義，包括角色和權限。 有效值包括 skipMembership、 copyAll、 ignoreSecurity。|  
|applyCompression|True|布林值，若為 true，表示壓縮將會套用期間同步處理作業。否則為 false。|  
  
## <a name="response"></a>回應  
 當命令執行成功，則傳回空的結果。 否則，傳回 XMLA 例外狀況。  
  
## <a name="usage-endpoints"></a>使用方式 （端點）  
 這個命令項目用在陳述式的[Execute Method &#40;XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)呼叫透過 XMLA 端點，以下列方式公開：  
  
-   以 XMLA 視窗中 SQL Server Management Studio (SSMS)  
  
-   為輸入檔案**叫用 ascmd** PowerShell cmdlet  
  
-   做為輸入到 SSIS 工作或 SQL Server Agent 作業  
  
 您可以從 SSMS 產生現成的指令碼，此命令，依序按一下 [同步處理資料庫] 對話方塊上的 [指令碼] 按鈕。  
  
 [ \[MS-SSAS T\]: QL Server Analysis Services 表格式 （SQL Server 技術通訊協定）](http://go.microsoft.com/fwlink/p/?LinkId=784855)文件包含區段 3.1.5.2.2 描述結構的 JSON 表格式中繼資料命令和物件。 目前，該文件涵蓋命令和功能尚未實作用於 TMSL 指令碼。 請參閱主題[表格式模型指令碼語言 &#40;TMSL &#41;參考](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)以釐清支援的項目  
  
## <a name="see-also"></a>請參閱＜  
 [表格式模型指令碼語言 &#40;TMSL&#41; 參考](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
