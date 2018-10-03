---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bbbf5cba908426d1890423f01dbe42c346b4c3ad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631899"
---
# <a name="mssqlserver9004"></a>MSSQLSERVER_9004
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|9004|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|LOG_CORRUPT|  
|訊息文字|在處理資料庫 '%.*ls' 的記錄檔時，發生錯誤。  If possible, restore from backup. 若備份無法使用，可能需要重建記錄檔。|  
  
## <a name="explanation"></a>說明  
在回復、復原或複寫期間處理記錄檔時發生錯誤。 這可能代表作業系統偵測到的錯誤，或是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 偵測到的內部一致性錯誤。  
  
## <a name="user-action"></a>使用者動作  
您可以執行下列其中一項動作來更正此錯誤：  
  
-   從備份進行還原。  
  
-   重建記錄檔。  
  
此外，請檢查系統事件和錯誤記錄檔，以找出可能造成問題的系統內部問題。  
  
