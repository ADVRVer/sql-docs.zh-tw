---
title: "對時態表進行資料分割 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 04/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: e76675099ab290d29231d434eb74e92b613185b7
ms.openlocfilehash: cb93e468300aea6a666ad04e9ce6ad20e1b85fc2
ms.contentlocale: zh-tw
ms.lasthandoff: 09/29/2017

---
# <a name="partitioning-with-temporal-tables"></a>對時態表進行資料分割
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  您可以各自在目前的資料表和記錄資料表上使用資料分割。 不過，您無法使用資料分割來變更沒有設定系統版本的資料內容。  
  
> [!NOTE]  
>  資料分割是 SQL Server 2016 在 Service Pack 1 和舊版以前的 Enterprise Edition 功能。 SQL Server 2016 Service Pack 1 所有版本和更新版本都支援資料分割。
  
-   **目前的資料表：**  
  
    -   當**SWITCH IN** 為 **SWITCH IN** 時， **SWITCH IN**目前的資料表可用來加速資料載入和查詢  
  
    -   **SYSTEM_VERSIONING** 為 **ON** 時不允許 **SWITCH OUT**  
  
-   **記錄資料表：**  
  
    -   當**SWITCH OUT** 為 **SWITCH OUT** 時，可執行從記錄資料表 **SWITCH OUT** to purge portions of h時，可執行從記錄資料表tory data that 時，可執行從記錄資料表 no longer relevant.  
  
    -   當**SWITCH IN** 為 **SWITCH IN** 時，不允許 **SWITCH IN** since it can invalidate temporal data cons時，不允許tency.  
  
## <a name="did-this-article-help-you-were-listening"></a>這篇文章對您有幫助嗎？ 我們會持續聽取您的意見  
 您要尋找哪些資訊？找到了嗎？ 我們會持續聽取您的意見來改進內容。 請將您的意見傳送到 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Partitioning%20with%20Temporal%20Tables%20page)  
  
## <a name="see-also"></a>另請參閱  
 [時態表](../../relational-databases/tables/temporal-tables.md)   
 [開始使用系統建立版本的時態表](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [時態表系統一致性檢查](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [時態表考量與限制](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [時態表安全性](../../relational-databases/tables/temporal-table-security.md)   
 [管理系統設定版本之時態表中的歷程記錄資料保留](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [系統版本設定時態表與記憶體最佳化資料表](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [暫存資料表中繼資料檢視和函數](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  

