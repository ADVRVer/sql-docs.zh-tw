---
title: 匯入從關聯式資料來源 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 44c4f0a5fbdaa64f2145113bf5135dad9acbddbb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62730739"
---
# <a name="import-from-a-relational-data-source-ssas-tabular"></a>從關聯式資料來源匯入 (SSAS 表格式)
  您可以使用 [資料表匯入精靈]，從各種關聯式資料庫匯入資料。 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]提供此精靈，位於 [模型]  功能表。 若要連接至資料來源，您必須先在電腦上安裝適當的提供者。 如需支援的資料來源和提供者的詳細資訊，請參閱 [支援的資料來源 &#40;SSAS 表格式&#41;](tabular-models/data-sources-supported-ssas-tabular.md)(支援的資料來源 (SSAS 表格式))。  
  
 [資料表匯入精靈] 支援從下列資料來源匯入資料：  
  
 **關聯式資料庫**  
  
-   Microsoft SQL Server 資料庫  
  
-   Microsoft SQL Azure  
  
-   Microsoft Access 資料庫  
  
-   Microsoft SQL Server Parallel Data Warehouse  
  
-   Oracle  
  
-   Teradata  
  
-   Sybase  
  
-   Informix  
  
-   IBM DB2  
  
-   OLE DB/ODBC  
  
 **多維度來源**  
  
-   Microsoft SQL Server Analysis Services Cube  
  
 [資料表匯入精靈] 不支援從 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 活頁簿匯入資料做為資料來源。  
  
### <a name="to-import-data-from-a-database"></a>從資料庫匯入資料  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[從資料來源匯入]**。  
  
2.  在 **[連接到資料來源]** 頁面上，選取要連接的資料庫類型，然後按 **[下一步]**。  
  
3.  請遵循 [資料表匯入精靈] 中的步驟來進行。 在後續頁面中，您即可選取特定的資料表及檢視，或使用 **[選取資料表和檢視表]** 頁面，或在 **[指定 SQL 查詢]** 頁面上建立 SQL 查詢，以套用篩選。  
  
## <a name="see-also"></a>另請參閱  
 [匯入資料 &#40;SSAS 表格式&#41;](import-data-ssas-tabular.md)   
 [支援的資料來源 &#40;SSAS 表格式&#41;](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
