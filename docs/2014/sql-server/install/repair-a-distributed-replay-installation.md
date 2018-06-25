---
title: 修復 Distributed 的 Replay 安裝 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8adf917831b33c1603b3c0c4a1e7b678900cf7dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36131433"
---
# <a name="repair-a-distributed-replay-installation"></a>修復 Distributed Replay 安裝
  修復 Distributed Replay 元件 (控制器或用戶端) 會執行下列動作：  
  
1.  再次於磁碟上安裝所有相關聯的檔案，並取代任何現有的檔案。  
  
2.  如果已移除對應的服務帳戶，則重新建立 Windows 服務帳戶。  
  
 您無法使用修復作業來加入或移除元件。 新增或移除元件，請核取或取消核取上的 功能樹狀目錄中的對應元件**特徵選取**頁面[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安裝程式。  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a>修復 Distributed Replay 的失敗安裝  
  
1.  從**啟動**功能表上，按一下 **控制台**，然後按兩下**新增或移除程式**。  
  
2.  選取[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中**解除安裝或變更程式**視窗中，然後在[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]對話方塊中，按一下 **修復**。  
  
3.  請依照下列中的步驟[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]精靈，然後在**選取功能**頁面上，選取您想要修復，然後按一下 [Distributed Replay 元件**下一步]。**。  
  
4.  完成 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝精靈，修復選取的 Distributed Replay 功能。  
  
  