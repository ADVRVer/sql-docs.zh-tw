---
title: sp_invalidate_textptr & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_invalidate_textptr_TSQL
- sp_invalidate_textptr
dev_langs:
- TSQL
helpviewer_keywords:
- sp_invalidate_textptr
ms.assetid: dd9920e1-7064-4c05-93d8-9303103fa1d6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9075b653b6cdb9baec70a182b560201efcb6c965
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724266"
---
# <a name="spinvalidatetextptr-transact-sql"></a>sp_invalidate_textptr (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  讓指定的同資料列文字指標失效，或者讓交易中所有的同資料列文字指標全部失效。 **sp_invalidate_textptr**可以只能用在同資料列文字指標。 這些指標是來自資料表的**資料列中的文字**啟用的選項。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_invalidate_textptr [ [ @TextPtrValue = ] textptr_value ]  
```  
  
## <a name="arguments"></a>引數  
 [  **@TextPtrValue=** ] *textptr_value*  
 這是即將失效的同資料列文字指標。 *textptr_value*已**varbinary (** 16 **)**，預設值是 NULL。 如果是 NULL， **sp_invalidate_textptr**讓交易中所有的資料列文字指標失效。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在每個資料庫的每項交易中，最多可以接受 1,024 個使用中的有效同資料列文字指標；不過，如果交易超出一個資料庫，每個資料庫就可以有 1,024 個同資料列文字指標。 **sp_invalidate_textptr**可用來使其失效的資料列文字指標，因此，可用空間，額外的資料列文字指標。  
  
 如需有關 text in row 選項的詳細資訊，請參閱 < [sp_tableoption &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)。  
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [Database Engine 預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)   
 [TEXTPTR &#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [TEXTVALID &#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)  
  
  
