---
title: 編輯類型對應（SybaseToSQL） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 513f071a-d5e6-4ed5-acca-269bf76323c5
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: cd8dfbd7aa4205424c45861f6ada1113f76d344e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029168"
---
# <a name="edit-type-mapping-sybasetosql"></a>編輯類型對應 (SybaseToSQL)
[**編輯類型對應**] 對話方塊可讓您指定如何在來源與目的地資料庫物件之間對應類型。  
  
您可以在數個位置存取此對話方塊：  
  
-   當您選取源資料庫或資料庫物件時，[**類型對應**] 索引標籤會出現在 [中繼資料] explorer 的右邊。 按一下 [**加入**] 以加入新的類型對應，或按一下 [**編輯**] 以變更現有的類型對應。  
  
-   在 [**工具**] 功能表上，選取 [**專案設定**] 或 [**預設專案設定**]。 在產生的對話方塊中，選取 [**類型對應**]。 按一下 [**加入**] 以加入新的類型對應，或按一下 [**編輯**] 以變更現有的類型對應。  
  
資料表特定類型對應會覆寫資料庫和專案類型對應。 資料庫特定對應會覆寫專案對應。  
  
## <a name="options"></a>選項  
**來源類型**  
選取要對應至[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料類型的源資料類型。  
  
如果資料類型的長度可變，下欄欄位會出現在 [**來源類型**] 底下：  
  
**From**  
指定此對應的最小長度。 例如，針對**Nchar**資料類型，您可以輸入10來指定此對應是針對從**Nchar （10）** 開始的範圍。  
  
**自**  
指定此對應的最大長度。 例如，針對**Nchar**資料類型，您可以輸入20來指定此對應是針對結束于**Nchar （20）** 的範圍。  
  
**目標型別**  
選取源[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料類型對應的資料類型。 當 SSMA 在中[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]建立資料表或預存程式時，源資料類型將會變更為此資料類型。  
  
如果資料類型是可變長度，下欄欄位會出現在 [**目標型別**] 底下：  
  
**取代為**  
指定此對應的目標長度。 例如，針對**Nvarchar**資料類型，您可以輸入20，指定指定的源資料類型應對應至**Nvarchar （20）**。  
  
