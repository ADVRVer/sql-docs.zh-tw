---
title: 資料表和資料行 |Microsoft 文件
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 10133b2843c01f16134c028140394247c2669236
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="tables-and-columns"></a>資料表與資料行 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  在您使用 [資料表匯入精靈] 將資料表和資料加入模型之後，即可開始使用資料表，包括加入新資料行、建立資料表之間的關聯性、定義可擴充資料的計算，以及在資料表中篩選及排序資料以便於檢視。  
  
 本主題的章節：  
  
-   [優點](#bkmk_benefits)  
  
-   [使用資料表和資料行](#bkmk_working)  
  
-   [相關工作](#bkmk_related_tasks)  
  
##  <a name="bkmk_benefits"></a> 優點  
 表格式模型中的資料表提供定義資料行及其他中繼資料的架構。 資料表包括：  
  
 **資料表定義**  
 資料表定義包含一組資料行。 可從資料來源匯入或手動加入資料行，例如導出資料行。  
  
 **資料表中繼資料**  
 關聯性、量值、角色、檢視方塊及貼上的資料，都是定義資料表內容中之物件的所有中繼資料。  
  
 **資料**  
 當您透過 [資料表匯入精靈] 或在導出資料行中建立新資料，第一次匯入資料表時，會在資料表資料行中擴展資料。 變更來源中的資料，或從記憶體中移除模型時，您必須執行處理作業將資料重新擴展到資料表中。  
  
##  <a name="bkmk_working"></a> 使用資料表和資料行  
 在模型設計師中，您不會直接建立新的模型資料表。 每當從其他資料來源匯入或複製資料時，都會為您自動建立新的索引標籤。 模型設計師中的每個索引標籤都包含一個資料表，其中可以包括以下項目：  
  
-   來自關聯式資料庫或其他非關聯式來源 (如 Analysis Services Cube) 的單一資料表或檢視表。  
  
-   從摘要或文字檔匯入的一組表格式資料。  
  
-   關聯式資料和表格式 (HTML) 資料的組合會複製並貼到資料表中。  
  
 當您匯入資料時，每一個資料表或檢視表、工作表或資料檔都會當做資料表加入至模型設計師。 您通常會從各種來源將資料加入到個別的索引標籤上，但是您可以使用 **[貼上]** 和 **[貼上新增]** 來合併單一資料表中的資料。 如需詳細資訊，請參閱[複製及貼上資料](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md)。  
  
 在您加入所需的資料之後，您可以建立資料表之間的其他關聯性、在其他資料表中查閱或參考相關的值，或者加入新的導出資料行來建立衍生的值。  
  
 如果您使用非常大型的資料集，您可能需要篩選而不顯示特定資料。 您可能也需要依不同順序排序資料。 透過模型設計師，您可以使用篩選、排序及隱藏功能顯示或隱藏整個資料行或特定資料。  
  
##  <a name="bkmk_related_tasks"></a> 相關工作  
  
|主題|Description|  
|-----------|-----------------|  
|[在資料表新增資料行](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)|描述如何將來源資料行加入至資料表定義。|  
|[刪除資料行](../../analysis-services/tabular-models/delete-a-column-ssas-tabular.md)|描述如何使用模型設計師或 [資料表屬性] 對話方塊，刪除模型資料表資料行。|  
|[變更資料表、資料行或資料列篩選對應](../../analysis-services/tabular-models/change-table-column-or-row-filter-mappings-ssas-tabular.md)|描述如何使用資料表預覽或 [編輯資料表屬性] 對話方塊中的 SQL 查詢編輯器，變更資料表、資料行或資料列篩選對應。|  
|[指定「標記為日期資料表」以搭配時間智慧使用](../../analysis-services/tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md)|描述如何使用 [標記為日期資料表] 對話方塊來指定日期資料表和唯一識別碼資料行。 DAX 公式中使用時間智慧函數時，必須指定日期資料表和唯一識別碼。|  
|[新增資料表](../../analysis-services/tabular-models/add-a-table-ssas-tabular.md)|描述如何透過使用現有的資料來源連接，從資料來源中加入資料表。|  
|[刪除資料表](../../analysis-services/tabular-models/delete-a-table-ssas-tabular.md)|描述如何刪除模型工作空間資料庫中不再需要的資料表。|  
|[重新命名資料表或資料行](../../analysis-services/tabular-models/rename-a-table-or-column-ssas-tabular.md)|描述如何重新命名資料表或資料行，以在模型中更容易識別。|  
|[設定資料行的資料類型](../../analysis-services/tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)|描述如何變更資料行的資料類型。 資料類型定義資料行中資料的儲存及呈現方式。|  
|[隱藏或凍結資料行](../../analysis-services/tabular-models/hide-or-freeze-columns-ssas-tabular.md)|描述如何隱藏您不想顯示的資料行，以及如何透過凍結 (鎖定) 某個區域中的特定資料行，以在捲動到模型其他區域時，讓某個模型區域保持可見。|  
|[導出資料行](../../analysis-services/tabular-models/ssas-calculated-columns.md)|本節中的主題描述如何使用導出資料行將彙總資料加入至模型。|  
|[篩選與排序資料](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)|本節中的主題描述如何使用模型設計師中的控制項篩選或排序資料。|  
  
  
