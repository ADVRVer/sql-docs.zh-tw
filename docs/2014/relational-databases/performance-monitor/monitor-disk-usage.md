---
title: 監視磁碟使用量 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 58c0251f9277b923b00a32a992761e976483ef8e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36034975"
---
# <a name="monitor-disk-usage"></a>監視磁碟使用量
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用 Microsoft Windows 作業系統輸入/輸出 (I/O) 呼叫，在您的磁碟上執行讀取和寫入作業。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會管理何時及如何執行磁碟 I/O，但是 Windows 作業系統會執行基礎 I/O 作業。 I/O 子系統包含了系統匯流排、磁碟控制卡、磁碟、磁帶機、光碟機和許多其他的 I/O 裝置。 磁碟 I/O 經常是造成系統瓶頸的原因。  
  
 監視磁碟活動涉及兩個重點：  
  
-   監視磁碟 I/O 與偵測額外的分頁方式  
  
-   隔離 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 建立的磁碟活動  
  
 如需詳細資訊，請參閱 [監視磁碟使用量](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)  
  
  