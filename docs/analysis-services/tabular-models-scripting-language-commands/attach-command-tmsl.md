---
title: 附加命令 (TMSL) |Microsoft 文件
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fcafff4ce1b5e87a9ca3e7933989ecbf9bf52bf3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="attach-command-tmsl"></a>附加命令 (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  將 Analysis Services 檔案附加至伺服器。  
  
  
## <a name="request"></a>要求  
  
```  
{   
   "attach":{   
      "folder":"C:\\Program Files\\Microsoft SQL Server\\MSAS13.Tabular\\OLAP\\Data\\",  
      "readWriteMode":"readOnly",  
      "password":"secret"  
   }  
}  
```  
  
 接受的 JSON 屬性附加命令如下。  
  
||||  
|-|-|-|  
|**屬性**|**預設值**|**說明**|  
|[資料庫]|[必要]|要附加的資料庫物件名稱。|  
|folder|[必要]|附加的資料庫所在的資料夾。|  
|密碼|Empty|要用來加密附加的資料庫中的機密密碼。|  
|readWriteMode|ReadWrite|列舉值，指出允許資料庫存取模式。<br /><br /> **列舉值如下所示：**<br /><br /> readWrite – 允許讀寫存取。<br /><br /> readOnly – 允許唯讀存取。<br /><br /> readOnlyExclusive – 允許唯讀狀態的獨佔存取權。|  
  
## <a name="response"></a>回應  
 當命令執行成功，則傳回空的結果。 否則，傳回 XMLA 例外狀況。  
  
## <a name="usage-endpoints"></a>使用方式 （端點）  
 這個命令項目用在陳述式的[Execute Method &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md)呼叫透過 XMLA 端點，以下列方式公開：  
  
-   以 XMLA 視窗中 SQL Server Management Studio (SSMS)  
  
-   為輸入檔案**叫用 ascmd** PowerShell cmdlet  
  
-   做為輸入到 SSIS 工作或 SQL Server Agent 作業  
  
 您可以從 SSMS 產生現成的指令碼，此命令，依序按一下 [附加資料庫] 對話方塊上的 [指令碼] 按鈕。  
  
 [ \[MS-SSAS T\]: QL Server Analysis Services 表格式 （SQL Server 技術通訊協定）](http://go.microsoft.com/fwlink/p/?LinkId=784855)文件包含區段 3.1.5.2.2 描述結構的 JSON 表格式中繼資料命令和物件。 目前，該文件涵蓋命令和功能尚未實作用於 TMSL 指令碼。 請參閱主題[表格式模型指令碼語言&#40;TMSL&#41;參考](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)以釐清支援的項目  

## <a name="see-also"></a>另請參閱  
 [表格式模型指令碼語言 &#40;TMSL&#41; 參考](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [附加和卸離 Analysis Services 資料庫](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
