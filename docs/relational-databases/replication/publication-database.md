---
title: "發行集資料庫 | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b183d388bd223e8371bb42f27072d6e636e53ce
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="publication-database"></a>發行集資料庫
  發行集資料庫是在發行者上的資料庫，它是要被複寫之資料和資料庫物件的來源。 必須啟用用於複寫的每個發行集資料庫。 當 **系統管理員 (sysadmin)** 固定伺服器角色的成員執行下列各項動作時，會啟用資料庫：  
  
-   使用新增發行集精靈在該資料庫上建立發行集。  
  
-   選取 **[發行者屬性]** 對話方塊中的資料庫。  
  
-   執行 **sp_replicationdboption** 並將 [發行]  選項 (適用於快照集或交易式發行集) 或 [合併發行]  選項 (適用於合併式發行集) 設定為 [True] 。  
  
## <a name="options"></a>選項  
 **資料庫**  
 選取包含您要發行之資料與資料庫物件的資料庫名稱。  
  
## <a name="see-also"></a>另請參閱  
 [發行資料和資料庫物件](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [建立發行集](../../relational-databases/replication/publish/create-a-publication.md)   
 [檢視及修改散發者和發行者屬性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  
