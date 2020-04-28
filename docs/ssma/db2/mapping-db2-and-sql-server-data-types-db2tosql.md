---
title: 對應 DB2 和 SQL Server 資料類型（DB2ToSQL） |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e7e939a8-5e76-4509-beaf-5acd1cab505e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1e9baab08f4295b2c51fd942f6153cc9425dd958
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68141013"
---
# <a name="mapping-db2-and-sql-server-data-types-db2tosql"></a>對應 DB2 和 SQL Server 資料類型（DB2ToSQL）
DB2 資料庫類型與[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫類型不同。 當您將 DB2 資料庫物件轉換[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]成物件時，您必須指定如何將資料類型從 DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]對應到。 您可以接受預設資料類型對應，也可以自訂對應，如下列各節所示。  
  
## <a name="default-mappings"></a>預設對應  
SSMA 有一組預設的資料類型對應。 如需預設對應的清單，請參閱[專案設定 &#40;類型對應&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md)。  
  
## <a name="type-mapping-inheritance"></a>類型對應繼承  
您可以在專案層級、物件類別目錄層級（例如所有預存程式）或物件層級自訂類型對應。 設定會繼承自較高的層級，除非它們在較低層級遭到覆寫。 例如，如果您在專案層級將**smallmoney**對應至**money** ，則專案中的所有物件都會使用此對應，除非您在物件或類別層級自訂對應。  
  
當您在 SSMA 中看到 [**型別對應**] 索引標籤時，背景會以色彩標示，以顯示要繼承的型別對應。 任何繼承的型別對應，型別對應的背景都是黃色，而在目前層級指定的任何對應則為白色。  
  
## <a name="customizing-data-type-mappings"></a>自訂資料類型對應  
下列程式顯示如何對應專案、資料庫或物件層級的資料類型：  
  
**對應資料類型**  
  
1.  若要自訂整個專案的資料類型對應，請開啟 [**專案設定**] 對話方塊：  
  
    1.  在 [**工具**] 功能表上，選取 [**專案設定**]。  
  
    2.  在左窗格中，選取 [**類型對應**]。  
  
        類型對應圖表和按鈕會出現在右窗格中。  
  
    或者，若要在資料庫、資料表、view 或預存程式層級自訂資料類型對應，請選取 [DB2 Metadata Explorer] 中的資料庫、物件類別或物件：  
  
    1.  在 DB2 Metadata Explorer 中，選取要自訂的資料夾或物件。  
  
    2.  在右窗格中，按一下 [**類型對應**] 索引標籤。  
  
2.  若要加入新的對應，請執行下列動作：  
  
    1.  按一下 **[新增]** 。  
  
    2.  在 [**來源類型**] 底下，選取要對應的 DB2 資料類型。  
  
    3.  如果類型需要長度，請在 [**來源**] 方塊中指定對應的最小資料長度，並在 [**到**] 方塊中指定最大資料長度。  
  
        這可讓您針對相同資料類型的較小且較大的值，自訂資料對應。  
  
    4.  在 [**目標型別**] 底下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]選取 [目標資料類型]。  
  
        某些類型需要目標資料類型長度。 如有需要，請在 [**取代為**] 方塊中輸入新的資料長度。  
  
    5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  若要修改資料類型對應，請執行下列動作：  
  
    1.  按一下 **[編輯]**。  
  
    2.  在 [**來源類型**] 底下，選取要對應的 DB2 資料類型。  
  
    3.  如果類型需要長度，請在 [**來源**] 方塊中指定對應的最小資料長度，並在 [**到**] 方塊中指定最大資料長度。  
  
        這可讓您針對相同資料類型的較小且較大的值，自訂資料對應。  
  
    4.  在 [**目標型別**] 底下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]選取 [目標資料類型]。  
  
        某些類型需要目標資料類型長度。 如有需要，請在 [**取代為**] 方塊中輸入新的資料長度，然後[!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  若要移除自訂資料類型對應，請執行下列動作：  
  
    1.  選取 [類型對應] 清單中的資料列，其中包含您想要移除的資料類型對應。  
  
    2.  按一下 [移除]****。  
  
        您無法移除繼承的對應。 不過，繼承的對應會由特定物件或物件類別上的自訂對應覆寫。  
  
## <a name="next-steps"></a>後續步驟  
遷移程式的下一個步驟是[評估報表 &#40;DB2ToSQL&#41;](../../ssma/db2/assessment-report-db2tosql.md)或將[DB2 架構轉換 &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md)。 如果您建立評量報告，DB2 物件會在評估期間自動轉換。  
  
## <a name="see-also"></a>另請參閱  
[將 DB2 資料庫移轉至 SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
