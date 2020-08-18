---
description: 編輯類型對應 (SybaseToSQL)
title: 編輯類型對應 (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 513f071a-d5e6-4ed5-acca-269bf76323c5
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 3f9f5e0f498dbe6a8fe45a9c80cbf3c512f04bac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492275"
---
# <a name="edit-type-mapping-sybasetosql"></a>編輯類型對應 (SybaseToSQL)
[ **編輯類型對應** ] 對話方塊可讓您指定如何在來源與目的地資料庫物件之間對應類型。  
  
您可以在幾個地方存取此對話方塊：  
  
-   當您選取源資料庫或資料庫物件時，[ **類型對應** ] 索引標籤會出現在中繼資料瀏覽器的右邊。 按一下 [ **加入** ] 以加入新的型別對應，或按一下 [ **編輯** ] 來變更現有的型別對應。  
  
-   在 [ **工具** ] 功能表上，選取 [ **專案設定** ] 或 [ **預設專案設定**]。 在 [產生的] 對話方塊中，選取 [ **類型對應**]。 按一下 [ **加入** ] 以加入新的型別對應，或按一下 [ **編輯** ] 來變更現有的型別對應。  
  
資料表特定的類型對應會覆寫資料庫和專案類型對應。 資料庫特定對應會覆寫專案對應。  
  
## <a name="options"></a>選項。  
**來源類型**  
選取要對應至資料類型的源資料類型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
如果資料類型的長度是可變的，則下欄欄位會出現在 [ **來源類型**] 下方：  
  
**From**  
指定此對應的最小長度。 例如，針對 **Nchar** 資料類型，您可以輸入10以指定此對應是針對從 **Nchar (10) **開始的範圍。  
  
**若要**  
指定此對應的最大長度。 例如，針對 **Nchar** 資料類型，您可以輸入20以指定此對應的範圍結束于 **Nchar (20) **。  
  
**目標型別**  
選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源資料類型所對應的資料類型。 當 SSMA 在中建立資料表或預存程式時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，源資料類型會變更為此資料類型。  
  
如果資料類型的長度為可變，則下欄欄位會出現在 [ **目標型別**] 下方：  
  
**Replace with**  
指定此對應的目標長度。 例如，對於 **Nvarchar** 資料類型，您可以輸入20以指定指定的源資料類型應該對應至 **Nvarchar (20) **。  
  
