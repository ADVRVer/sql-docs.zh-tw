---
title: MSSQL_ENG020574 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef099fbc6cdeace66b2b06cf1bf494b762346589
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68092125"
---
# <a name="mssqleng020574"></a>MSSQL_ENG020574
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|20574|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|訂閱者 '%s' 訂閱的發行項 '%s' (在發行集 '%s' 中)，未通過資料驗證。|  
  
## <a name="explanation"></a>說明  
 訂閱者端的資料是依據發行者端的資料進行驗證，而資料不相符，因此驗證失敗。 如需驗證的相關資訊，請參閱 [Validate Replicated Data](../../relational-databases/replication/validate-data-at-the-subscriber.md)。  
  
## <a name="user-action"></a>使用者動作  
 我們建議您執行下列動作：  
  
-   判斷驗證失敗的原因。  
  
-   更正導致失敗的根本問題。  
  
-   重新初始化訂閱或透過其他方法，讓資料聚合。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤和事件參考 &#40;複寫&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
