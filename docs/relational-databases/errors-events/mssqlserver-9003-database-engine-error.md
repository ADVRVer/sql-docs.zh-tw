---
title: MSSQLSERVER_9003 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eb3fcdb8bc7921c8321cc25ec9380143e7f68a68
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118354"
---
# <a name="mssqlserver9003"></a>MSSQLSERVER_9003
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|9003|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|LOG_INVALID_LSN|  
|訊息文字|傳遞到資料庫 '%.*ls' 記錄檔掃描的記錄檔掃描號碼 %S_LSN 無效。 這個錯誤可能表示資料損毀或記錄檔 (.ldf) 不符合資料檔案 (.mdf)。 如果是在複寫期間發生這個錯誤，請重新建立發行集。 否則，若該問題造成啟動失敗，則請從備份進行還原。|  
  
## <a name="explanation"></a>說明  
某個元件將無效的記錄序號傳遞給資料庫的記錄檔管理員。 這個問題的原因可能是複寫、損毀或主要資料檔案與記錄檔之間的不一致。  
  
## <a name="user-action"></a>使用者動作  
如果是在複寫期間發生這個錯誤，請重新建立發行集。 否則，請從備份進行還原。  
  
