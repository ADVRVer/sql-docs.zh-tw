---
title: "編輯類型對應 (AccessToSQL) |Microsoft 文件"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 7f9d9530-6c04-41d9-bbe7-d91820a30066
caps.latest.revision: 4
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2cfe289d367eee5d33177f8170e4be2919870ada
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="edit-type-mapping-accesstosql"></a>編輯類型對應 (AccessToSQL)
**編輯類型對應** 對話方塊可讓您指定來源和目的地的資料庫物件之間如何對應型別。  
  
您可以存取此對話方塊，在幾個地方：  
  
-   當您選取來源資料庫或資料庫物件**類型對應**右邊的 [中繼資料總管] 索引標籤會出現。 按一下**新增**加入新的型別對應，或按一下**編輯**若要變更現有的型別對應。  
  
-   在**工具**功能表上，選取**專案設定**或**預設專案設定**。 在 [結果] 對話方塊中，選取**類型對應**。 按一下**新增**加入新的型別對應，或按一下**編輯**若要變更現有的型別對應。  
  
特定資料表的型別對應會覆寫資料庫，和專案類型對應。 特定資料庫的對應覆寫專案對應。  
  
## <a name="options"></a>選項。  
**來源類型**  
選取來源資料類型對應至[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]資料型別。  
  
如果資料類型是可變長度，下列欄位會出現在**來源類型**:  
  
**來源**  
指定針對此對應的最小長度。 例如，對於**文字**資料類型，您可以輸入 10，以指定此對應是範圍開始**text(10)**。  
  
**若要**  
指定此對應的最大長度。 例如，對於**文字**資料類型，您可以輸入 20 來指定此對應的結束時間範圍**text(20)**。  
  
**目標類型**  
選取[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]來源資料類型對應的資料類型。 SSMA 當建立資料表或預存程序中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]，來源資料類型會變更為此資料類型。  
  
如果資料類型是可變長度，下列欄位會出現在**目標類型**:  
  
**Replace with**  
指定針對此對應的目標長度。 例如，對於**nvarchar**資料類型，您可以輸入 20 指定指定之來源資料類型應該對應至**nvarchar （20)**。  
  

