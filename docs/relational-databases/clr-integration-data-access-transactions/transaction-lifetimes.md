---
title: 事務存留期 |微軟文件
description: 瞭解 SQL Server CLR 整合中的事務存留期。 在 Transact-SQL 儲存過程中啟動的事務與託管代碼中啟動的事務不同。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 1fed737c644ebb241a5761fffd2409c2556d28ea
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487487"
---
# <a name="transaction-lifetimes"></a>交易存留期間
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  利用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序啟動的交易以及利用 Managed 程式碼啟動的交易間有一個重要的差異：Common Language Runtime (CLR) 程式碼無法在進入或離開 CLR 引動過程時讓交易狀態不平衡。 請注意此差異的下列含意：  
  
-   在 CLR 框架內部啟動的交易必須認可或回復，否則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在離開框架時會產生錯誤。  
  
-   外部交易無法在 CLR 程式碼內部認可或回復。  
  
-   嘗試認可未在相同程序中啟動的交易時，會造成執行階段錯誤。  
  
-   嘗試回滾未在同一過程中啟動的事務會導致事務停止回應(防止發生任何其他副作用操作)。 交易會停止，直到 CLR 程式碼超出範圍為止。 請注意，當您在程序內部偵測到錯誤，而且想要確認整個交易結束時，這可能相當實用。  
  
## <a name="see-also"></a>另請參閱  
 [CLR 整合和交易](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
