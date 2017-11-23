---
title: "卸離命令 (TMSL) |Microsoft 文件"
ms.custom: 
ms.date: 05/30/2017
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
ms.assetid: 413b49cb-ea8f-415c-a059-ce692b7771a1
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a379c50635dce40c90efebbeaae662ee778b964c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="detach-command-tmsl"></a>卸離命令 (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  中斷連結的伺服器從 Analysis Services 資料庫。  
  
## <a name="request"></a>要求  
  
```  
{   
   "detach": {    
      "database":"AdventureWorksDW2014",  
      "password": "secret"  
   }  
}  
```  
  
 接受的 JSON 屬性卸離命令如下。  
  
||||  
|-|-|-|  
|**屬性**|**預設值**|**說明**|  
|[資料庫]|[必要]|要卸離的資料庫物件的名稱。|  
|密碼|Empty|要用來加密卸離的資料庫中的機密密碼。|  
  
## <a name="response"></a>回應  
 當命令執行成功，則傳回空的結果。 否則，傳回 XMLA 例外狀況。  
  
## <a name="usage-endpoints"></a>使用方式 （端點）  
 這個命令項目用在陳述式的[Execute Method &#40;XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)呼叫透過 XMLA 端點，以下列方式公開：  
  
-   以 XMLA 視窗中 SQL Server Management Studio (SSMS)  
  
-   為輸入檔案**叫用 ascmd** PowerShell cmdlet  
  
-   做為輸入到 SSIS 工作或 SQL Server Agent 作業  
  
 您可以從 SSMS 產生現成的指令碼，此命令，依序按一下 [卸離] 對話方塊上的 [指令碼] 按鈕。  
  
 [ \[MS-SSAS T\]: QL Server Analysis Services 表格式 （SQL Server 技術通訊協定）](http://go.microsoft.com/fwlink/p/?LinkId=784855)文件包含區段 3.1.5.2.2 描述結構的 JSON 表格式中繼資料命令和物件。 目前，該文件涵蓋命令和功能尚未實作用於 TMSL 指令碼。 請參閱主題 ([表格式模型指令碼語言 &#40;TMSL &#41;參考](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) 以釐清支援的項目。  

## <a name="see-also"></a>請參閱＜  
 [表格式模型指令碼語言 &#40;TMSL&#41; 參考](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [附加和卸離 Analysis Services 資料庫](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
