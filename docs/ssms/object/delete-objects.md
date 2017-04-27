---
title: "刪除物件 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 053e53c609786f9ba9193c5dd2f70c58ec00eba3
ms.lasthandoff: 04/11/2017

---
# <a name="delete-objects"></a>刪除物件
使用此對話方塊來刪除資料庫或資料庫物件。  
  
## <a name="uielement-list"></a>UIElement 清單  
**要刪除的物件**  
顯示將要刪除之物件的名稱、類型、擁有者和狀態，以及有關執行期間發生錯誤的任何訊息。  
  
> [!NOTE]  
> 在資料庫上執行 [刪除] 相當於在 [!INCLUDE[tsql](../../includes/tsql_md.md)] 中發出 DROP DATABASE。  
  
**顯示相依性**  
按一下即可同時顯示相依於目前所選取物件的物件，以及目前物件相依的物件 (向上和向下相依性)。 [顯示相依性] 對話方塊中所顯示的資訊是唯讀的。  
  
> [!NOTE]  
> [顯示相依性] 按鈕並不會出現在所有類型的資料庫物件上。 若要檢視相依性，但[顯示相依性] 按鈕無法使用時，請以滑鼠右鍵按一下物件總管中的物件，然後按一下 [檢視相依性]。  
  
**刪除資料庫的備份與還原記錄資訊**  
只出現於資料庫已刪除時，此核取方塊會導致主旨資料庫的備份與還原記錄從 **msdb** 資料庫中刪除。  
  
**關閉現有的連接**  
只出現於資料庫已刪除時，此核取方塊會結束主旨資料庫的連接。  
  

