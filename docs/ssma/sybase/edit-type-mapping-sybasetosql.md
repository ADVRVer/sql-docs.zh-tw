---
title: 編輯類型對應 (SybaseToSQL) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 513f071a-d5e6-4ed5-acca-269bf76323c5
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 148922b21f3ce8de90315654524fe21e6e53581d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="edit-type-mapping-sybasetosql"></a>編輯類型對應 (SybaseToSQL)
**編輯類型對應** 對話方塊可讓您指定來源和目的地的資料庫物件之間如何對應型別。  
  
您可以存取此對話方塊，在幾個地方：  
  
-   當您選取來源資料庫或資料庫物件**類型對應**右邊的 [中繼資料總管] 索引標籤會出現。 按一下**新增**加入新的型別對應，或按一下**編輯**若要變更現有的型別對應。  
  
-   在**工具**功能表上，選取**專案設定**或**預設專案設定**。 在 [結果] 對話方塊中，選取**類型對應**。 按一下**新增**加入新的型別對應，或按一下**編輯**若要變更現有的型別對應。  
  
特定資料表的型別對應會覆寫資料庫，和專案類型對應。 特定資料庫的對應覆寫專案對應。  
  
## <a name="options"></a>選項  
**來源類型**  
選取來源資料類型對應至[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]資料型別。  
  
如果資料類型是可變長度，下列欄位會出現在**來源類型**:  
  
**來源**  
指定針對此對應的最小長度。 例如，對於**nchar**資料類型，您可以輸入 10，以指定此對應是範圍開始**nchar(10)**。  
  
**若要**  
指定此對應的最大長度。 例如，對於**nchar**資料類型，您可以輸入 20 來指定此對應的結束時間範圍**nchar(20)**。  
  
**目標類型**  
選取[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]來源資料類型對應的資料類型。 SSMA 當建立資料表或預存程序中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]，來源資料類型會變更為此資料類型。  
  
如果資料類型是可變長度，下列欄位會出現在**目標類型**:  
  
**Replace with**  
指定針對此對應的目標長度。 例如，對於**nvarchar**資料類型，您可以輸入 20 指定指定之來源資料類型應該對應至**nvarchar （20)**。  
  
