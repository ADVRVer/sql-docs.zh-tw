---
title: sp_cursorprepexec (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursorprepexec_TSQL
- sp_cursorprepexec
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorprepexec
ms.assetid: 8094fa90-35b5-4cf4-8012-0570cb2ba1e6
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 378a389780e8af6ed966c4e0757352b16fbc0dd1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33240378"
---
# <a name="spcursorprepexec-transact-sql"></a>sp_cursorprepexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  編譯提交之資料指標陳述式或批次的計畫，然後建立及擴展資料指標。 sp_cursorprepexec 會結合 sp_cursorprepare 和 sp_cursorexecute 的功能。 這個程序的叫用方式是在表格式資料流 (TDS) 封包中指定 ID = 5。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_cursorprepexec prepared handle OUTPUT, cursor OUTPUT, params , statement , options  
    [ , scrollopt [ , ccopt [ , rowcount ] ] ]  
```  
  
## <a name="arguments"></a>引數  
 *已備妥控制代碼*  
 是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]產生準備*處理*識別項。 *已備妥控制代碼*是必要的傳回**int**。  
  
 *cursor*  
 這是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產生的資料指標識別碼。 *資料指標*處理這個資料指標，例如 sp_cursorfetch 的所有後續程序上都必須提供必要參數。  
  
 *params*  
 識別參數化的陳述式。 *Params*變數的定義會替代陳述式中的參數標記。 *params*是必要的參數呼叫**ntext**， **nchar**，或**nvarchar**輸入值。  
  
> [!NOTE]  
>  使用**ntext**字串做為輸入值時*stmt*參數化和*scrollopt* PARAMETERIZED_STMT 值為 ON。  
  
 *陳述式*  
 定義資料指標結果集。 *陳述式*參數是必要而且會呼叫**ntext**， **nchar**或**nvarchar**輸入值。  
  
> [!NOTE]  
>  是指定 stmt 值的規則與 sp_cursoropen，發生例外狀況的相同， *stmt*字串資料類型必須是**ntext**。  
  
 *options*  
 傳回資料指標結果集資料行描述的選擇性參數。 *選項*必須符合下列需求**int**輸入值。  
  
|Value|Description|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
 *scrollopt*  
 捲動選項。 *scrollopt*是需要下列其中一個選擇性參數**int**輸入值。  
  
|Value|Description|  
|-----------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
|0x10|FAST_FORWARD|  
|0x1000|PARAMETERIZED_STMT|  
|0x2000|AUTO_FETCH|  
|0x4000|AUTO_CLOSE|  
|0x8000|CHECK_ACCEPTED_TYPES|  
|0x10000|KEYSET_ACCEPTABLE|  
|0x20000|DYNAMIC_ACCEPTABLE|  
|0x40000|FORWARD_ONLY_ACCEPTABLE|  
|0x80000|STATIC_ACCEPTABLE|  
|0x100000|FAST_FORWARD_ACCEPTABLE|  
  
 因為要求的選項不適用於所定義的資料指標的可能性 *\<stmt >*，這個參數會當做輸入和輸出。 在這類情況下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會指派適合的類型並修改這個值。  
  
 *ccopt*  
 並行控制選項。 *ccopt*是需要下列其中一個選擇性參數**int**輸入值。  
  
|Value|Description|  
|-----------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS (之前稱為 LOCKCC)|  
|0x0004|**開放式**（之前稱為 OPTCC）|  
|0x0008|OPTIMISTIC (之前稱為 OPTCCVAL)|  
|0x2000|ALLOW_DIRECT|  
|0x4000|UPDT_IN_PLACE|  
|0x8000|CHECK_ACCEPTED_OPTS|  
|0x10000|READ_ONLY_ACCEPTABLE|  
|0x20000|SCROLL_LOCKS_ACCEPTABLE|  
|0x40000|OPTIMISTIC_ACCEPTABLE|  
|0x80000|OPTIMISITC_ACCEPTABLE|  
  
 如同*scrollpt*，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可以指派不同的值與要求。  
  
 *資料列計數*  
 這是選擇性參數，表示要搭配 AUTO_FETCH 使用的提取緩衝區資料列數目。 預設為 20 個資料列。 *資料列計數*當指派為輸入值與傳回值時，表現。  
  
|當做輸入值|當做傳回值|  
|--------------------|---------------------|  
|當指定 AUTO_FETCH 與 FAST_FORWARD 資料指標*rowcount*代表要放入提取緩衝區資料列數目。|代表結果集中的資料列數目。 當*scrollopt*指定 AUTO_FETCH 值時， *rowcount*傳回提取到提取緩衝區的資料列數目。|  
  
## <a name="return-code-values"></a>傳回碼值  
 如果*params*未參數化陳述式會傳回 NULL 值。  
  
## <a name="see-also"></a>另請參閱  
 [sp_cursoropen &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorexecute &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursorprepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorprepare-transact-sql.md)   
 [sp_cursorfetch &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
