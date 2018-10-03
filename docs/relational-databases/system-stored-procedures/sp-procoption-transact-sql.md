---
title: sp_procoption & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_procoption
- sp_procoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_procoption
ms.assetid: 6f0221bd-70b4-4b04-b15d-722235aceb3c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0213e831f6613acc0ce5cc0a802240c2e3979fc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772336"
---
# <a name="spprocoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  設定或清除自動執行預存程序。 每當啟動一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，就會執行一個設為自動執行的預存程序。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>引數  
 [  **@ProcName =** ] **'***程序***'**  
 是用來設定選項的程序的名稱。 *程序*已**nvarchar(776)**，沒有預設值。  
  
 [  **@OptionName =** ] **'***選項***'**  
 這是您要設定的選項名稱。 唯一的值* 選項*是**啟動**。  
  
 [  **@OptionValue =** ] **'***值***'**  
 這是指是否選項設為 on (**，則為 true**或**上**) 或 [關閉]  (**false**或**關閉**)。 *值*已**varchar(12)**，沒有預設值。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或錯誤號碼 (失敗)  
  
## <a name="remarks"></a>備註  
 啟動程序必須處於**主要**資料庫，而且不能包含 INPUT 或 OUTPUT 參數。 預存程序會在所有資料庫皆完成復原時執行時，並會在啟動時記錄「已完成復原操作」訊息。  
  
## <a name="permissions"></a>Permissions  
 需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會設定程序自動執行。  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';   
```  
  
 下列範例會停止程序自動執行。  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';   
```  
  
## <a name="see-also"></a>另請參閱  
 [執行預存程序](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
