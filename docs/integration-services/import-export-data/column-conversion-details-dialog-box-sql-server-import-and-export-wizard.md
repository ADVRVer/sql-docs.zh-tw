---
title: 資料行轉換詳細資料對話方塊 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5341dac153f3bd9cc90d1abe43aa4dc2f8319f78
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2018
ms.locfileid: "35332172"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>資料行轉換詳細資訊對話方塊 (SQL Server 匯入和匯出精靈)
  如果您在 [檢閱資料類型對應]  頁面上按兩下個別資料行的資料列，[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈] 會顯示 [資料行轉換詳細資訊]  對話方塊。 在此頁面上，您可以檢閱個別資料行的詳細轉換資訊。 此資訊包括下列項目。
-   來源和目的地的資料行資料類型。
-   如果需要轉換，則是精靈將會執行的資料類型轉換。
-   精靈用來判斷所需資料類型轉換的資料類型對應檔案。 

## <a name="screen-shot-of-the-column-conversion-details-page"></a>[資料行轉換詳細資訊] 頁面的螢幕擷取畫面 
 下列螢幕擷取畫面會在使用者按兩下 [檢閱資料類型對應]  頁面上的資料列之後，顯示精靈的 [資料行轉換詳細資訊]  對話方塊。 若要透過另一種方式查看 [檢閱資料類型對應]  頁面，請參閱 [檢閱資料類型對應](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)。
 
在此範例中，您會看到下列項目。
-   來源 SQL Server 資料表中的 `PersonID` 資料行類型為 `int`。 精靈會藉由參考資料類型對應檔案 MSSQLToSSIS10.xml，將此類型對應至 SQL Server Integration Services (SSIS) `DT_I4` 資料類型，也就是四位元組帶正負號的整數。
-   目的地 SQL Server 資料表中的 `PersonID` 資料行類型也是 `int`。 精靈會將此類型對應至相同的 SSIS 資料類型。
-   精靈判斷「此資料行不需要進行轉換」。
 
  
 ![[匯入和匯出精靈] 的資料行轉換頁面](../../integration-services/import-export-data/media/column-conversion.png "[匯入和匯出精靈] 的資料行轉換頁面") 
  
## <a name="whats-next"></a>下一步  
 在您檢閱資料行轉換詳細資訊並按一下 [確定] 之後，[資料行轉換詳細資訊]  對話方塊會讓您回到 [檢閱資料類型對應]  頁面。 如需詳細資訊，請參閱 [檢閱資料類型對應](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)。  

## <a name="see-also"></a>另請參閱
[SQL Server 匯入及匯出精靈的資料類型對應](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
