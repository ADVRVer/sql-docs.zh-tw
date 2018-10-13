---
title: 物件定義在表格式模型指令碼語言 (TMSL) |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: de968c32f8c00132157a5b1b7a6682adc7148446
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851743"
---
# <a name="tmsl-reference---tabular-objects"></a>TMSL 參考 - 表格式物件
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  應用程式的建立、 取用，或管理表格式資料庫或連接到 SQL Server 2016 Analysis Services 執行個體以表格式模式，可以使用表格式模型指令碼語言 」 (TMSL) 命令，並以 JSON 格式的物件表示法。  
  
 這篇文章說明在 SQL Server Management Studio、 SQL Server Data Tools (SSDT) 和 AMO PowerShell 所產生的指令碼中使用的 TMSL 結構描述的主要物件。  
  
 物件的 json 定義，而且用於 TMSL 命令，例如 Create、 Alter 和刪除。 請參閱[表格式模型指令碼語言中的命令&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md)如需命令的清單。  
  
## <a name="main-objects"></a>主要物件  
 下表是 TMSL 指令碼中最常使用的物件清單。  
  
|||  
|-|-|  
|[資料庫物件&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|定義表格式資料庫相容性層級 1200年或更高版本，以相同的層級的模型為基礎。|  
|[模型物件&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|定義表格式模型 1200年或更高的相容性層級。|  
|[資料來源物件&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|當模型處於 DirectQuery 模式時，使用期間匯入 以載入模型中，或傳遞查詢的資料來源中定義的連接。|  
|[Tables 物件&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|指定模型的資料表。|  
|[資料分割物件&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|定義資料表資料列集，包括導出的資料表的儲存的體。|  
|[關聯性物件&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|定義資料表之間的關聯性。|  
|[角色物件&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|定義權限、 成員資格，以及控制存取的安全性篩選的資料和作業。|  
  
## <a name="see-also"></a>另請參閱  
 [表格式模型指令碼語言 &#40;TMSL&#41; 參考](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
