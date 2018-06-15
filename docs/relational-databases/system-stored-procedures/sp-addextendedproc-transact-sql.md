---
title: sp_addextendedproc (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addextendedproc_TSQL
- sp_addextendedproc
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addextendedproc
ms.assetid: c0d4b47b-a855-451e-90e5-5fb2d836ebfa
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2083d370479fa19049a083ef401574f21740929c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239788"
---
# <a name="spaddextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  登錄新的名稱，擴充預存程序[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用 [CLR 整合](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>引數  
 [  **@functname =** ] **'***程序***'**  
 這是在動態連結程式庫 (DLL) 內所要呼叫的函數名稱。 *程序*是**nvarchar （517)**，沒有預設值。 *程序*可以選擇性地包括擁有者名稱的形式*owner.function*。  
  
 [  **@dllname =** ] **'***dll***'**  
 這是包含這個函數的 DLL 名稱。 *dll*是**varchar （255)**，沒有預設值。 建議您指定 DLL 的完整路徑。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 無  
  
## <a name="remarks"></a>備註  
 建立擴充預存程序之後，必須新增至[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用**sp_addextendedproc**。 如需詳細資訊，請參閱[將擴充預存程序加入至 SQL Server](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md)。  
  
 只有在執行此程序**主要**資料庫。 從資料庫中不是執行擴充預存程序**主要**，限定擴充預存程序的名稱**主要**。  
  
 **sp_addextendedproc**將項目加入[sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)擴充預存程序的目錄檢視，登錄新的名稱[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 它也會加入中的項目[sys.extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md)目錄檢視。  
  
> [!IMPORTANT]  
>  在升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之後，沒有用完整路徑來登錄的現有 DLL 無法運作。 若要修正這個問題，請使用**sp_dropextendedproc**要取消登錄 DLL，並再重新註冊與**sp_addextendedproc**，指定完整路徑。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色可以執行**sp_addextendedproc**。  
  
## <a name="examples"></a>範例  
 下列範例會將**xp_hello**擴充預存程序。  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>另請參閱  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
