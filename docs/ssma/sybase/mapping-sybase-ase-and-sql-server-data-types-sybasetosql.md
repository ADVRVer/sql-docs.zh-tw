---
description: 對應 Sybase ASE 和 SQL Server 資料類型 (SybaseToSQL)
title: 對應 Sybase ASE 和 SQL Server 資料類型 (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Mapping Sybase ASE Schemas to SQL Server Schemas
- Type Mapping Settings
ms.assetid: 784365d3-df4e-47ab-8ee0-d8392b52f510
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5a7e1ba17822d339e5ae40e6e6b5828191ce84ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463170"
---
# <a name="mapping-sybase-ase-and-sql-server-data-types-sybasetosql"></a>對應 Sybase ASE 和 SQL Server 資料類型 (SybaseToSQL)
Sybase 自我調整 Server Enterprise (ASE) 資料庫類型與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 Azure SQL Database 類型不同。 當您將 ASE 資料庫物件轉換成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 Sql azure 物件時，您必須指定如何將資料類型從 ASE 對應至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 sql azure。 您可以接受預設資料類型對應，也可以自訂對應，如下列各節所示。  
  
## <a name="default-mappings"></a>預設對應  
SSMA 具有一組預設的資料類型對應。 如需預設對應清單，請參閱 [&#40;類型對應的專案設定&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)。  
  
## <a name="type-mapping-inheritance"></a>類型對應繼承  
您可以在專案層級、物件類別層級 (（例如所有預存程式) 或物件層級）自訂類型對應。 除非在較低層級進行覆寫，否則設定會繼承自較高的層級。 例如，如果您在專案層級將 **smallmoney** 對應至 **money** ，則專案中的所有物件都會使用此對應，除非您自訂物件類別層級或物件層級的對應。  
  
當您在 SSMA 中查看 [ **類型對應** ] 索引標籤時，背景會以色彩標示，以顯示要繼承的類型對應。 類型對應的背景為黃色，表示任何繼承的型別對應，以及在目前層級指定之任何對應的白色。  
  
## <a name="customizing-data-type-mappings"></a>自訂資料類型對應  
下列程式顯示如何對應專案、資料庫或物件層級的資料類型。  
  
**對應資料類型**  
  
1.  若要自訂整個專案的資料類型對應，請開啟 [ **專案設定** ] 對話方塊：  
  
    1.  在 [ **工具** ] 功能表上，選取 [ **專案設定**]。  
  
    2.  在左窗格中，選取 [ **類型對應**]。  
  
        型別對應圖表和按鈕會出現在右窗格中。  
  
    或者，若要自訂資料庫、資料表、視圖或預存程式層級的資料類型對應，請在 [Sybase 中繼資料瀏覽器] 中選取資料庫、物件類別或物件：  
  
    1.  在 [Sybase 中繼資料瀏覽器] 中，選取您要自訂的資料夾或物件。  
  
    2.  在右窗格中，按一下 [ **類型對應** ] 索引標籤。  
  
2.  若要加入新的對應，請執行下列動作：  
  
    1.  按一下 [新增] 。  
  
    2.  在 [ **來源類型**] 下，選取要對應的 ASE 資料類型。  
  
    3.  如果類型需要長度，請在 [ **從** ] 方塊中指定對應的最小資料長度，並在 [ **到** ] 方塊中指定對應的最大資料長度。  
  
        這可讓您針對相同資料類型的較小且較大值，自訂資料對應。  
  
    4.  在 [ **目標型別**] 下，選取 [目標] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [SQL Azure] 資料類型。  
  
        某些類型需要目標資料類型長度。 如有需要，請在 [ **取代成** ] 方塊中輸入新的資料長度。  
  
    5.  按一下 [確定]。  
  
3.  若要編輯資料類型對應，請執行下列動作：  
  
    1.  按一下 **[編輯]** 。  
  
    2.  在 [ **來源類型**] 下，選取要對應的 ASE 資料類型。  
  
    3.  如果類型需要長度，請在 [ **從** ] 方塊中指定對應的最小資料長度，並在 [ **到** ] 方塊中指定對應的最大資料長度。  
  
        這可讓您針對相同資料類型的較小且較大值，自訂資料對應。  
  
    4.  在 [ **目標型別**] 下，選取 [目標] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [SQL Azure] 資料類型。  
  
        某些類型需要目標資料類型長度。 如有需要，請在 [ **取代成** ] 方塊中輸入新的資料長度，然後按一下 **[確定]**。  
  
4.  若要移除自訂資料類型對應，請執行下列動作：  
  
    1.  在 [類型對應] 清單中選取包含您想要移除之資料類型對應的資料列。  
  
    2.  按一下 **[移除]** 。  
  
        您無法移除繼承的對應。 不過，繼承的對應會由特定物件或物件類別目錄上的自訂對應覆寫。  
  
## <a name="next-steps"></a>後續步驟  
遷移程式的下一個步驟是 [建立評定報告](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) ，或 [將 Sybase ASE 資料庫物件轉換成 SQL Server 或 SQL Azure 語法](converting-sybase-ase-database-objects-sybasetosql.md)。 如果您建立評量報告，則會在評估期間自動轉換 Sybase ASE 物件。  
  
## <a name="see-also"></a>另請參閱  
[將 Sybase ASE 資料庫移轉至 SQL Server Azure SQL Database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
