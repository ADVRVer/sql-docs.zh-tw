---
title: "增加或停用已封鎖的處理序閾值 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b392ec86b64ee41864dfa3c2067e549031b31900
ms.lasthandoff: 04/11/2017

---
# <a name="increase-or-disable-blocked-process-threshold"></a>增加或停用 Blocked Process Threshold
  此規則會檢查 blocked process threshold 選項設定為 0 (已停用) 還是設定為高於或等於 5 (秒) 的值。 將 blocked process threshold 選項設定為 1 到 4 的值會造成死結監視器不斷執行。 1 到 4 之間的值應該只用於疑難排解，絕不能在沒有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務與支援中心協助的情形下，長期使用或用在實際執行環境。  
  
## <a name="best-practices-recommendations"></a>最佳做法建議  
 若要解決這個問題，請將 blocked process threshold 選項設定為 5 (秒) 或更高的值，或是將此值設定為 0 來停用 blocked process threshold。 若要將 blocked process threshold 設定為 `5` 秒的值，請執行以下陳述式：  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a>詳細資訊  
 [已封鎖的處理序臨界值伺服器組態選項](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來監視和強制最佳做法](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
