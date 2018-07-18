---
title: 結束定義域管理活動 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b7e67308da4240f223f414ddf5e6080f0b5726e6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328458"
---
# <a name="end-the-domain-management-activity"></a>結束定義域管理活動
  此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中完成、關閉或取消定義域管理活動。 定義域管理不是由精靈執行，所以可以從定義域管理活動的任何頁面使用底下所述的控制項。  
  
## <a name="end-domain-management"></a>結束定義域管理  
 **[完成]**  
 按一下以完成定義域管理。 隨即顯示快顯視窗，讓您執行下列動作：  
  
-   **是 - 發行知識庫並結束**：將會發行知識庫，供目前使用者或其他使用者使用。 知識庫不會鎖定，知識庫狀態 (在知識庫資料表中) 將會設為空白，而且定義域管理和知識探索活動可供使用。 您會返回 [開啟知識庫] 畫面。  
  
-   **否 - 儲存知識庫工作並結束**：將會儲存您的工作，知識庫會保持鎖定，而且知識庫狀態將會設為 [工作中]。 定義域管理和知識探索活動都可供使用。 您會返回首頁。  
  
-   **取消 - 留在目前畫面**：快顯視窗將會關閉，而且您會返回 [定義域管理] 畫面。  
  
 **取消**  
 按一下以結束 [定義域管理] 活動，不儲存工作並返回 DQS 首頁。  
  
 **關閉**  
 按一下以儲存工作，並返回 DQS 首頁。 知識庫會鎖定，而且在 **[開啟知識庫]** 畫面中知識庫資料表的知識庫狀態將會是 **[定義域管理]**。 在按一下 **[關閉]** 之後，若要執行 [知識探索] 活動，您必須返回 **[定義域管理]** 畫面，按一下 **[完成]**，然後按一下 **[是]** 發行知識庫，或按一下 **[否]** 儲存知識庫工作並結束。  如需開啟鎖定之知識庫的詳細資訊，請參閱＜ [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)＞。  
  
  
