---
title: "發行者屬性 - 發行者，發行集資料庫 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.pubproperties.pubdb.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cc86424019df085038fffd9b076576eb9c717024
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="publisher-properties---publisher-publication-databases"></a>發行者屬性 - 發行者，發行集資料庫
  **[發行者屬性]** 對話方塊的 **[發行集資料庫]** 頁面，可讓 **系統管理員 (sysadmin)** 固定伺服器角色中的使用者啟用資料庫供複寫。 啟用資料庫不會發行此資料庫；不過，它允許該資料庫之 **db_owner** 固定資料庫角色中的任何使用者在資料庫上建立一個或多個發行集。  
  
## <a name="options"></a>選項  
 **異動**  
 選取此核取方塊即可讓 **db_owner** 固定資料庫角色中的使用者，在資料庫中建立快照式發行集或交易式發行集。  
  
 **合併式**  
 選取此核取方塊即可讓 **db_owner** 固定資料庫角色中的使用者，在資料庫中建立合併式發行集。  
  
## <a name="see-also"></a>另請參閱  
 [檢視及修改散發者和發行者屬性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [屬性參考 &#40;複寫&#41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  
