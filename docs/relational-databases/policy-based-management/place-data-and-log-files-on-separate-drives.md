---
title: "將資料檔和記錄檔放在不同的磁碟機上 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6d105c0a058a5256904c2bfc2442b48c5f3c51eb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="place-data-and-log-files-on-separate-drives"></a>將資料檔和記錄檔放在不同的磁碟機上
  此規則會檢查資料檔和記錄檔是否放在不同的邏輯磁碟機上。 將資料檔和記錄檔放在相同的裝置上可能會造成該裝置的競爭情況，並產生效能不佳的情況。 將這些檔案放在不同的磁碟機上可允許同時針對資料檔和記錄檔發生 I/O 活動。  
  
## <a name="recommendations"></a>建議  
 當您建立新的資料庫時，請針對資料和記錄指定個別的磁碟機。 若要在建立資料庫之後移動檔案，必須讓該資料庫離線。 請使用下列其中一種方法來移動檔案：  
  
> [!NOTE]  
>  這個原則無法透過掛接點偵測個別的實體裝置  
  
-   使用具有 WITH MOVE 選項的 RESTORE DATABASE 陳述式從備份還原資料庫。  
  
-   卸離然後附加資料庫，為資料和記錄裝置指定不同的位置。  
  
-   執行具有 MODIFY FILE 選項的 ALTER DATABASE 陳述式然後重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體，以指定新的位置。  
  
## <a name="for-more-information"></a>詳細資訊  
 [移動資料庫檔案](../../relational-databases/databases/move-database-files.md)  
  
 [移動使用者資料庫](../../relational-databases/databases/move-user-databases.md)  
  
 [資料庫卸離與附加 &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來監視和強制最佳做法](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
