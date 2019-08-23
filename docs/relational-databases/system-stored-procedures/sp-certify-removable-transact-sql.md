---
title: sp_certify_removable (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_certify_removable_TSQL
- sp_certify_removable
dev_langs:
- TSQL
helpviewer_keywords:
- sp_certify_removable
ms.assetid: ca12767f-0ae5-4652-b523-c23473f100a1
author: stevestein
ms.author: sstein
ms.openlocfilehash: c39665f54a915282a6c59fe7d57b24d0cde0a5e7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68045935"
---
# <a name="sp_certify_removable-transact-sql"></a>sp_certify_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  確認已正確設定資料庫的抽取式媒體散發作業，並向使用者報告任何問題。  
  
> **重要！！** [!INCLUDE[ssNoteDepFutureAvoid](../../t-sql/statements/create-database-sql-server-transact-sql.md) instead.  
  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_certify_removable [ @dbname= ] 'dbname'  
     [ , [ @autofix = ] 'auto' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @dbname = ] 'dbname'` 指定要驗證的資料庫。 *dbname*已**sysname**。  
  
`[ @autofix = ] 'auto'` 資料庫和所有資料庫物件的擁有權提供給系統管理員，並卸除任何使用者建立的資料庫使用者和非預設權限。 *自動*已**nvarchar(4)** ，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 如果資料庫已正確設定， **sp_certify_removable**執行下列：  
  
-   將資料庫設為離線，以便複製檔案。  
  
-   更新所有資料表的統計資料，以及報告任何擁有權或使用者問題。  
  
-   將資料檔案群組標示為唯讀，以便將這些檔案複製到唯讀媒體中。  
  
 系統管理員必須是資料庫和所有資料庫物件的擁有者。 系統管理員是已知的使用者執行的所有伺服器上存在於[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]且可預期稍後散發和安裝資料庫時。  
  
 如果您執行**sp_certify_removable**不含**自動**值，且會傳回任何下列條件的相關資訊：  
  
-   系統管理員不是資料庫擁有者。  
  
-   有使用者建立的使用者存在。  
  
-   系統管理員並未擁有資料庫中的所有物件。  
  
-   授與了非預設的權限。  
  
 您可以利用下列方式來更正這些狀況：  
  
-   使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]工具和程序，然後執行**sp_certify_removable**一次。  
  
-   只要執行**sp_certify_removable**具有**自動**值。  
  
 請注意，這個預存程序只會檢查使用者和使用者權限。 您可以將群組加入資料庫中，以及將權限授與這些群組。 如需詳細資訊，請參閱 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)的相關資訊。  
  
## <a name="permissions"></a>Permissions  
 執行權限會限制為成員的**sysadmin**固定的伺服器角色。  
  
## <a name="examples"></a>範例  
 下列範例會證明 `inventory` 資料庫已完成移除的準備。  
  
```  
EXEC sp_certify_removable inventory, AUTO;  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料庫卸離和附加 &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_create_removable &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-removable-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
