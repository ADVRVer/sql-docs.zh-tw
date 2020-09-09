---
description: sp_defaultlanguage (Transact-SQL)
title: sp_defaultlanguage (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_defaultlanguage
- sp_defaultlanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultlanguage
ms.assetid: 908d01cc-e704-45d9-9e85-d2df6da3e6f5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5eb94ea64b22f233d1c7c1e5d508fc0704f931ab
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549852"
---
# <a name="sp_defaultlanguage-transact-sql"></a>sp_defaultlanguage (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的預設語言。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_defaultlanguage [ @loginame = ] 'login'   
     [ , [ @language = ] 'language' ]   
```  
  
## <a name="arguments"></a>引數  
`[ @loginame = ] 'login'` 這是登入名稱。 *login* 是 **sysname**，沒有預設值。 *登* 入可以是現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入或 Windows 使用者或群組。  
  
`[ @language = ] 'language'` 這是登入的預設語言。 *language* 是 **sysname**，預設值是 Null。 *語言* 在伺服器上必須是有效的語言。 如果未指定 *語言* ，則 *語言* 會設定為伺服器預設語言;預設語言是由 **sp_configure** 設定變數 **預設語言**所定義。 變更伺服器的預設語言，並不會變更現有登入的預設語言。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_defaultlanguage** 會呼叫支援其他選項的 ALTER LOGIN。 如需變更其他登入預設值的詳細資訊，請參閱 [ALTER login &#40;transact-sql&#41;](../../t-sql/statements/alter-login-transact-sql.md)。  
  
 請使用 SET LANGUAGE 陳述式來變更目前工作階段的語言。 使用 @ @LANGUAGE 函數可顯示目前的語言設定。  
  
 如果登入的預設語言已從伺服器卸除，該登入便會取得伺服器的預設語言。 **sp_defaultlanguage** 無法在使用者自訂交易內執行。  
  
 在伺服器上安裝之語言的相關資訊會顯示在 **sys.sys語言** 類別目錄檢視中。  
  
## <a name="permissions"></a>權限  
 需要 ALTER ANY LOGIN 權限。  
  
## <a name="examples"></a>範例  
 下列範例會利用 `ALTER LOGIN`，將登入 `Fathima` 的預設語言改成「阿拉伯文」。 這是慣用的方法。  
  
```  
ALTER LOGIN Fathima WITH DEFAULT_LANGUAGE = Arabic;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [安全性預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET 陳述式 &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [sys.sys語言 &#40;Transact-sql&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
