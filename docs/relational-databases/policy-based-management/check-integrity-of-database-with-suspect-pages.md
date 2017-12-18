---
title: "檢查具有可疑頁面的資料庫是否完整 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6999acc42dac211b14b22489fc6941043f98d48
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>檢查具有可疑頁面的資料庫是否完整
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 此規則會檢查資料庫狀態設定為有疑問的使用者資料庫。 當 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 讀取包含 824 錯誤的資料庫頁面時，該頁面會被視為有疑問、它的頁面識別碼會記錄在 msdb 內的 suspect_pages 資料表中，而且包含此頁面的資料庫會設定為有疑問。  
  
 錯誤 824 表示讀取作業期間偵測到邏輯一致性錯誤。 這個錯誤通常表示錯誤 I/O 子系統元件所造成的資料損毀。 這是嚴重的錯誤狀況，且可能會損及資料庫的完整性，所以必須立即更正。  
  
## <a name="best-practices-recommendations"></a>最佳做法建議  
  
-   請檢閱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以取得這個資料庫之 824 錯誤的詳細資料。  
  
-   完成完整資料庫一致性檢查 ([DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md))。  
  
-   實作定義在 [MSSQLSERVER_824](http://go.microsoft.com/fwlink/?LinkId=81397)中的使用者動作。  
  
## <a name="for-more-information"></a>詳細資訊  
 [管理 suspect_pages 資料表 &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
