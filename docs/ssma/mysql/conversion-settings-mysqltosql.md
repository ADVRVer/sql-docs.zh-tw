---
title: "轉換設定 (MySQLToSQL) |Microsoft 文件"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f551cf6e-1575-4206-9cca-975b5b43a6b8
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 29e0343f6f4e254a8171cb1d44084201af34d7d9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="conversion-settings-mysqltosql"></a>轉換設定 (MySQLToSQL)
**'設定'**索引標籤可讓使用者設定節點層級設定。 [] 索引標籤會位於下列 Metabase 節點：  
  
-   資料庫節點  
  
-   函式類別  
  
-   函式節點  
  
-   資料表類別  
  
-   在資料表節點  
  
## <a name="specifications"></a>規格：  
**設定** 索引標籤有兩個使用者的設定、 viz。:  
  
1.  函式轉換  
  
2.  轉換資料表  
  
這些設定可根據 Metabase 節點類型。 例如，函式轉換相關的設定將不會位於資料表節點  
  
> [!NOTE]  
> -   使用者所做的變更將在 [專案] 工作區中儲存為個別的喜好設定檔案。  
> -   這個檔案的副檔名會是**ccprefs**。  
  
1.  **函式轉換設定：**  
  
    1.  此索引標籤包含**'Force 函式轉換'**選項。 此選項可以有下列四個值之一：  
  
        -   根據專案設定 [繼承] 轉換  
  
        -   永遠將轉換成函式  
  
        -   永遠將轉換的程序  
  
        -   根據專案設定轉換  
  
    2.  根據設定，函式將會轉換為函式或預存程序。  
  
    3.  使用者所做的設定會儲存在重疊的喜好設定檔案上按一下**套用** 按鈕。  
  
2.  **資料表轉換設定：**  
  
    1.  此索引標籤包含**隱藏 ROWID 輔助的資料行產生**選項。 此選項可以有下列四個值之一：  
  
        -   根據專案設定 [繼承] 轉換  
  
        -   是  
  
        -   否  
  
        -   根據專案設定轉換  
  
    2.  如果**'Yes'**，這項設定會禁止 ROWID 輔助的資料行建立目標資料表上建立。  
  
    3.  使用者所做的設定會儲存在重疊的喜好設定檔案上按一下**套用** 按鈕。  
  
## <a name="see-also"></a>請參閱＜  
[專案設定 （轉換） (MySQL to SQL)](http://msdn.microsoft.com/en-us/7ad5fe44-6445-4ba8-a457-5af792631f11)  
  
