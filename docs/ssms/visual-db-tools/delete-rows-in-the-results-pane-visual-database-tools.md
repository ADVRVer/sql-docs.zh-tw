---
title: 刪除結果窗格中的資料列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- removing rows
- row removal [SQL Server], Visual Database Tools Results pane
- row deletions [SQL Server], Visual Database Tools Results pane
- Query Designer [SQL Server], Results pane
- deleting rows
- Results pane
ms.assetid: a1147905-fe4a-4fac-b576-a17622477e66
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 63f480358f0f6fffea0e63c4c2ff06a3993eee73
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105787"
---
# <a name="delete-rows-in-the-results-pane-visual-database-tools"></a>刪除結果窗格中的資料列 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
若要刪除資料庫中的資料錄，請刪除 [結果] 窗格中的資料列。 若要刪除所有的資料列，請使用刪除查詢。 如需詳細資訊，請參閱 [建立製成資料表查詢 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)。 如果只是要從 [結果] 窗格移除資料列，請變更查詢的準則。 如需詳細資訊，請參閱 [指定搜尋準則 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)。  
  
### <a name="to-delete-a-row-or-rows"></a>若要刪除資料列  
  
1.  在 [結果] 窗格中，選取要刪除的資料列左邊的方塊。  
  
2.  按下 DELETE 鍵。  
  
3.  在詢問確認的訊息方塊中，按一下 [是]。  
  
> [!CAUTION]  
> 用這種方式刪除的資料列，會永久自資料庫移除，無法重新叫用。  
  
> [!NOTE]  
> 如果選取的資料列中有任何一個無法從資料庫刪除，所有的資料列將都不會刪除，而且您會接收到通知哪個資料列無法刪除的訊息。  
  
## <a name="see-also"></a>另請參閱  
[建立製成資料表查詢 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)  
[指定搜尋準則 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
