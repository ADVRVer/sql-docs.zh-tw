---
title: MSSQLSERVER_3176 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4e9f05297542a3b06c2c2350d0206e5c90ca8f29
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "34320449"
---
# <a name="mssqlserver3176"></a>MSSQLSERVER_3176
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件識別碼|3176|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|LDDB_FILE_CLAIM|  
|訊息文字|檔案 '%ls' 已被 '%ls'(%d) 和 '%ls'(%d) 所要求。 WITH MOVE 子句可以用來重新放置一個或多個檔案。|  
  
## <a name="explanation"></a>說明  
試圖使用單一檔案從事多種用途。  
  
### <a name="possible-causes"></a>可能的原因  
檔案名稱正由另一資料庫使用中。  
  
## <a name="user-action"></a>使用者動作  
請將資料庫檔案還原到其他位置。 在 RESTORE 陳述式中，使用 WITH MOVE 子句搬移每個檔案。 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 開啟 [還原資料庫] 對話方塊，在 [選項] 頁面的 [將資料庫檔案還原為] 方格中變更檔案位置。  
  
## <a name="see-also"></a>另請參閱  
[將資料庫還原到新位置 &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[將檔案還原到新位置 &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
