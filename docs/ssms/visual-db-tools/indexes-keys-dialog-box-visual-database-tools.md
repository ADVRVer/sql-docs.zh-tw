---
title: "索引 - 索引鍵對話方塊 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdtsql.chm:65539
- vdt.ppg.indexeskeys
ms.assetid: 9e4060ba-80c3-468f-bccb-e12e99f672c2
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1fa2fa79f818c344f9228dffe500fbe96236954b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="indexes---keys-dialog-box-visual-database-tools"></a>索引 - 索引鍵對話方塊 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] 使用此對話方塊可建立或修改索引、主索引鍵和唯一鍵。 若要存取此對話方塊，請開啟具有索引或索引鍵之資料表的資料表定義，在資料表定義方格上按一下滑鼠右鍵，再按一下 [索引/索引鍵]。  
  
> [!NOTE]  
> 如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) 或 SQL Server 管理物件 (SMO) 變更結構描述。 使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。 您無法卸除已發行的物件，因此結構描述變更將會失敗。  
  
## <a name="options"></a>選項。  
**選取的主/唯一索引鍵或索引**  
列出現有的主索引鍵或唯一鍵和索引。 選取一項，以便在右邊方格中顯示其屬性。 如果清單是空的，表示此資料表沒有任何定義的項目。  
  
**[加入]**  
建立新的主索引鍵、唯一鍵或索引。  
  
**刪除**  
刪除在 [選取的主/唯一索引鍵或索引] 清單中選取的索引鍵或索引。  
  
**一般類別目錄**  
展開時會顯示 [資料行]、[是唯一的] 和 [類型] 屬性。  
  
**資料行**  
列出索引鍵或索引中資料行的選擇排序次序，並且提供存取可在其中定義排序次序的對話方塊。 若要顯示對話方塊，可按一下 [資料行]，再按一下屬性欄位右邊的省略符號按鈕 (…)。  
  
**是唯一的**  
指示此索引或索引鍵中輸入的資料是否必須是唯一的。 這不適用於 XML 索引。  
  
**型別**  
指定在 [選取的主/唯一索引鍵或索引] 清單中選取的項目是唯一的索引鍵、主索引鍵或索引。 對於主索引鍵，此欄位是唯讀的。  
  
**識別類別目錄**  
展開時會顯示 [名稱] 和 [描述] 的屬性欄位。  
  
**名稱**  
顯示索引鍵或索引的名稱。 在建立新索引時，會根據 [資料表設計師] 作用中視窗的資料表，給予預設的名稱。 您可以隨時變更名稱。  
  
**說明**  
提供描述索引鍵或索引的位置。 若要寫入更詳細的描述，請按一下 [描述]，再按屬性欄位右邊的省略符號按鈕 (**…**)。 如此便可提供較大的區域以寫入文字。  
  
**資料表設計工具類別目錄**  
展開時會顯示 [建立成 CLUSTERED] 的資訊。  
  
**建立成 CLUSTERED**  
使索引鍵或索引成為叢集。 資料表中只能有一個叢集索引。 資料表中的資料會依照叢集索引的順序儲存。 如需詳細資訊，請參閱 [建立叢集索引](http://msdn.microsoft.com/en-us/47148383-c2c7-4f08-a9e4-7016bf2d1d13) 和 [建立非叢集索引](http://msdn.microsoft.com/en-us/9402029a-1227-46c4-93aa-c2122eb1b943)。  
  
**資料空間規格**  
展開時會顯示 [(資料空間類型)]、[檔案群組或資料分割配置名稱] 和 [資料分割資料行清單] 的資訊。  
  
**(資料空間類型)**  
指示此索引或索引鍵是否屬於檔案群組或資料分割配置。  
  
**檔案群組或資料分割配置名稱**  
顯示項目儲存位置的檔案群組名稱或資料分割配置名稱。  
  
**資料分割資料行清單**  
顯示加入資料分割資料行函數的逗號分隔之資料行清單。 如果在 [(資料空間類型)] 欄位中選取檔案群組，則無法使用。  
  
**填滿規格**  
展開時會顯示 [填滿因數]\(Fill Factor) 和 [索引頁預留空間] 的資訊。  
  
**填滿因數**  
指定系統可以填滿的索引分葉層級頁百分比。 當一頁填滿時，系統必須分割此頁才能加入新資料，因此會降低效能。  
  
-   值 100 表示頁面已填滿。 如此便需要最少的儲存空間。 只有在資料未進行任何變更時 (例如，在唯讀的資料表上)，才應該使用此設定。  
  
-   較小的值會在資料頁中會留下較多空白空間。 如此索引增加時就不需要分割資料頁，但需要較多的存放空間。  
  
**索引頁預留空間**  
指示在資料增加時，此索引中的中繼頁是否提供與 [填滿因素] 中指定的相同空白空間 (填補) 百分比。  
  
**忽略重複的索引鍵**  
指定在資料列的索引鍵值等於大量插入作業期間插入的現有索引鍵值時，會發生哪些狀況。 如果您選擇：  
  
-   [是]：[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 會發出警告，忽略違規的連入資料列，並嘗試插入其餘的資料列。  
  
-   [否]：[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 會發出錯誤訊息，並復原整個大量插入作業。  
  
**包含的資料行**  
顯示構成索引鍵之所有資料行的逗號分隔之名稱清單。 子索引鍵資料行只能在非叢集索引中指定。 如果是 XML 索引，這個屬性就會隱藏。  
  
**是停用的**  
指示此索引是否停用。 這是一個唯讀屬性。 如果已在 Visual Database Tools 外部停用索引，則這個屬性只能設定為 [是]。  
  
**是全文檢索索引鍵**  
指定此索引是否為全文檢索索引鍵。 如需有關全文檢索索引鍵的詳細資訊，請參閱《SQL Server 線上叢書》。 如果是 XML 索引，這個屬性就會隱藏。  
  
**允許頁面鎖定**  
指定是否在此索引中允許頁面層級的鎖定。 允許或不允許頁面層級的鎖定會影響資料庫效能。 建議設定為 [是]。  
  
**重新計算統計資料**  
指定基礎 [!INCLUDE[ssDE](../../includes/ssde_md.md)] 是否會在建立索引時計算新的統計資料。 重新計算統計資料會減緩索引的建置，但是非常有利於改善查詢效能。  
  
**允許資料列鎖定**  
指定是否在此索引中允許資料列層級的鎖定。 允許或不允許資料列層級的鎖定會影響資料庫效能。 建議設定為 [是]。  
  
## <a name="see-also"></a>另請參閱  
[使用條件約束 (Visual Database Tools)](http://msdn.microsoft.com/en-us/637098af-2567-48f8-90f4-b41df059833e)  
[使用索引鍵 (Visual Database Tools)](http://msdn.microsoft.com/en-us/31fbcc9f-2dc5-4bf9-aa50-ed70ec7b5bcd)  
  
