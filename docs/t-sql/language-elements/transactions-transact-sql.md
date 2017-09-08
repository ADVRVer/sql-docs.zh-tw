---
title: "交易 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Transactions
- Transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactions [SQL Server]
- transactions [SQL Server], about transactions
- UOW [SQL Server]
- unit of work [SQL Server]
ms.assetid: 1485c375-921a-42af-a871-bb333cc08d3e
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8660d0ac8d6205a94fdab24f41e41bac40a8671e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="transactions-transact-sql"></a>交易 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  交易是單一工作單元。 如果交易成功，便會確定交易期間所修改的所有資料，且會成為資料庫中永久的內容。 如果交易發現錯誤，必須取消或回復，便會清除所有的資料修改。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 採用下列交易模式來操作。  
  
 自動認可交易  
 每個個別陳述式都是一項交易。  
  
 明確交易  
 每項交易都是用 BEGIN TRANSACTION 陳述式來明確啟動，用 COMMIT 或 ROLLBACK 陳述式來明確結束。  
  
 隱含交易  
 在上一項交易完成時，隱含地啟動新的交易，但每項交易都用 COMMIT 或 ROLLBACK 陳述式來明確地完成。  
  
 批次範圍的交易  
 僅適用於 Multiple Active Result Sets (MARS)，在 MARS 工作階段下啟動的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 外顯或隱含交易會變成批次範圍的交易。 當批次完成時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會自動回復未認可或回復之批次範圍的交易。  
  
## <a name="in-this-section"></a>本節內容  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供下列交易陳述式。  
  
|||  
|-|-|  
|[開始分散式交易](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)|[ROLLBACK TRANSACTION](../../t-sql/language-elements/rollback-transaction-transact-sql.md)|  
|[開始交易](../../t-sql/language-elements/begin-transaction-transact-sql.md)|[ROLLBACK WORK](../../t-sql/language-elements/rollback-work-transact-sql.md)|  
|[認可交易](../../t-sql/language-elements/commit-transaction-transact-sql.md)|[儲存交易](../../t-sql/language-elements/save-transaction-transact-sql.md)|  
|[認可工作](../../t-sql/language-elements/commit-work-transact-sql.md)||  
  
## <a name="see-also"></a>另請參閱  
 [SET IMPLICIT_TRANSACTIONS &#40;TRANSACT-SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
