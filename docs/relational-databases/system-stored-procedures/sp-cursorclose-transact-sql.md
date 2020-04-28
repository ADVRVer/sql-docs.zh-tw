---
title: sp_cursorclose （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_close_TSQL
- sp_cursor_close
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorclose
ms.assetid: d9b7b44d-cdff-456e-97df-7031a3b9beb6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 543e8c0b41000ec2afe9ab07aef08aa86967c2ce
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108562"
---
# <a name="sp_cursorclose-transact-sql"></a>sp_cursorclose (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  關閉並取消配置資料指標，以及釋放所有相關聯的資源;也就是說，它會卸載用於支援索引鍵集或靜態資料**指標**的臨時表。 sp_cursorclose 的叫用方式是在表格式資料流 (TDS) 封包中指定 ID = 9。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>引數  
 *cursor*  
 這是由[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所產生並由 sp_cursoropen 程式所傳回的資料指標*控制碼*值。 *cursor*是針對**int**輸入值呼叫的必要參數。  
  
> [!NOTE]  
>  輸入值 -1 會套用到目前連接的所有資料指標上。  
  
## <a name="remarks"></a>備註  
 如果在資料指標已關閉或指定了不正確控制碼之後執行程式，則資料*指標*會傳回錯誤訊息。  
  
 RPC 狀態指出整體成功或失敗。  
  
 DONE 資料列計數一定是 0。  
  
## <a name="see-also"></a>另請參閱  
 [sp_cursoropen &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
