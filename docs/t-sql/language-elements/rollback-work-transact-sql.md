---
title: "ROLLBACK WORK (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROLLBACK WORK
- ROLLBACK_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transaction rollbacks [SQL Server]
- erasing data modifications [SQL Server]
- ROLLBACK WORK statement
- roll back transactions [SQL Server]
- rolling back transactions, ROLLBACK WORK
- savepoints [SQL Server]
ms.assetid: 2071dbd3-53d5-4510-be8d-26e80f2553b4
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d1a4eadefc731dd403b7900af4b5d2e32d4c358d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="rollback-work-transact-sql"></a>ROLLBACK WORK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  將使用者指定的交易回復到交易的開頭。  
  
 
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
ROLLBACK [ WORK ]  
[ ; ]  
```  
  
## <a name="remarks"></a>備註  
 這個陳述式的功能與 ROLLBACK TRANSACTION 相同，不過 ROLLBACK TRANSACTION 接受使用者自訂的交易名稱。 不論是否指定了選擇性的 WORK 關鍵字，這個 ROLLBACK 語法與 ISO 相容。  
  
 當建立巢狀交易，ROLLBACK WORK 一律會回復最外層的 BEGIN TRANSACTION 陳述式，並遞減 @@TRANCOUNT系統函式設為 0。  
  
## <a name="permissions"></a>Permissions  
 ROLLBACK WORK 權限預設會授與任何有效的使用者。  
  
## <a name="see-also"></a>另請參閱  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [認可工作 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  

