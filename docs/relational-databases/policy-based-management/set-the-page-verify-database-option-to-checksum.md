---
title: "將 PAGE_VERIFY 資料庫選項設定為 CHECKSUM | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "最佳做法 [Database Engine]"
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# 將 PAGE_VERIFY 資料庫選項設定為 CHECKSUM
  這個規則會檢查 PAGE_VERIFY 資料庫選項是否設定為 CHECKSUM。 當針對 PAGE_VERIFY 資料庫選項啟用 CHECKSUM 時，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會針對整頁的內容計算總和檢查碼，並在將頁面寫入磁碟時，於頁首中儲存值。 從磁碟讀取頁面時，會重新計算總和檢查碼，並與頁首所儲存的總和檢查碼值作比較。 如此有助於提供高層級的資料檔完整性。  
  
## 最佳做法建議  
 將 PAGE_VERIFY 資料庫選項設定為 CHECKSUM。  
  
## 詳細資訊  
 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)  
  
  