---
title: MSSQLSERVER_17884 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17884 (Database Engine error)
ms.assetid: 8d05ba05-3f71-4dc3-bd81-2ea5ac9fe843
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 40e33482a0d5f8ec4f01bc86d319ac243d550b23
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780722"
---
# <a name="mssqlserver_17884"></a>MSSQLSERVER_17884
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|17884|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SRV_SCHEDULER_DEADLOCK|  
|訊息文字|在過去的 %d 秒內，工作者執行緒未在節點 %d 上收取到指派給處理序的新查詢。 這種狀況可能是由封鎖或長時間執行的查詢所造成，且可能會對用戶端的回應時間造成負面影響。 請使用 "max worker threads" 組態選項以增加允許的執行緒數目，或最佳化目前執行中的查詢。  SQL 處理序使用率: %d%%。 系統閒置率: %d%%。|  
  
## <a name="explanation"></a>說明  
每個排程器都沒有進度的徵兆，而且可能是由於死結所造成，因為沒有任何執行緒可以進行及/或沒有新的工作可挑選和處理。 如果處理序使用率很低，則電腦上的其他處理序可能會導致伺服器處理序 CPU 資源用盡。  
  
## <a name="user-action"></a>使用者動作  
判斷為何產生封鎖而且沒有任何進度，並據以解決此狀況。 如果處理序使用率很低，請檢查其他處理序所造成的系統負載。  
  
