---
title: "將 AUTO_CLOSE 資料庫選項設定為 OFF | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
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
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f7e0a92a62abd1239b9f0d45d37c68e490505826
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="set-the-autoclose-database-option-to-off"></a>將 AUTO_CLOSE 資料庫選項設定為 OFF
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 這個規則會檢查 AUTO_ CLOSE 選項是否設定為 OFF。 當 AUTO_CLOSE 設定為 ON 時，這個選項可能會造成經常存取之資料庫的效能降低，因為在每一個連接之後都會增加開啟和關閉資料庫的負擔。 在每一個連接之後，AUTO_CLOSE 也會排清程序快取。  
  
## <a name="best-practices-recommendations"></a>最佳做法建議  
 如果經常存取資料庫，請將此資料庫的 AUTO_CLOSE 選項設定為 OFF。  
  
## <a name="for-more-information"></a>詳細資訊  
 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來監視和強制最佳做法](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
