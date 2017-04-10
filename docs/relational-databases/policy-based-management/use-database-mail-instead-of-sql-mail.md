---
title: "使用 Database Mail 而非 SQL Mail | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "最佳做法 [Database Engine]"
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# 使用 Database Mail 而非 SQL Mail
  此規則會檢查 sys.configurations 目錄檢視，以判斷 SQL Mail XP 的整個伺服器組態選項是否設定為 ON。  
  
## 最佳做法建議  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的未來版本將移除 SQL Mail。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 若要傳送郵件，請使用 Database Mail。  
  
 SQL Mail 會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的同處理序執行。 如果 SQL Mail 關閉，伺服器也會關閉。 Database Mail 會在不同處理序的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外部執行，它可以擴充，而且不需要在實際執行伺服器上安裝延伸的 MAPI 用戶端元件。  
  
## 詳細資訊  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
## 另請參閱  
 [使用原則式管理來監視和強制最佳做法](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  