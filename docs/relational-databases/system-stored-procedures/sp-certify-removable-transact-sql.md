---
description: sp_certify_removable (Transact-SQL)
title: sp_certify_removable (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9f5bf1f0fd8a73948c2cc85937af4bc4c5ec7ffc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493409"
---
# <a name="sp_certify_removable-transact-sql"></a>sp_certify_removable (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  確認已正確設定資料庫的抽取式媒體散發作業，並向使用者報告任何問題。  
  
> **重要！！** [!請改為包含[s s](../../t-sql/statements/create-database-sql-server-transact-sql.md) 。  
  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_certify_removable [ @dbname= ] 'dbname'  
     [ , [ @autofix = ] 'auto' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @dbname = ] 'dbname'` 指定要驗證的資料庫。 *dbname* 是 **sysname**。  
  
`[ @autofix = ] 'auto'` 將資料庫和所有資料庫物件的擁有權提供給系統管理員，並卸載任何使用者建立的資料庫使用者和非預設許可權。 *auto* 是 **Nvarchar (4) **，預設值是 Null。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 如果資料庫已正確設定， **sp_certify_removable** 會執行下列動作：  
  
-   將資料庫設為離線，以便複製檔案。  
  
-   更新所有資料表的統計資料，以及報告任何擁有權或使用者問題。  
  
-   將資料檔案群組標示為唯讀，以便將這些檔案複製到唯讀媒體中。  
  
 系統管理員必須是資料庫和所有資料庫物件的擁有者。 系統管理員是已知的使用者，存在於所有執行的伺服器上， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 且在稍後散發和安裝資料庫時可能會存在。  
  
 如果您在沒有**auto**值的情況下執行**sp_certify_removable** ，它會傳回下列任何條件的相關資訊：  
  
-   系統管理員不是資料庫擁有者。  
  
-   有使用者建立的使用者存在。  
  
-   系統管理員並未擁有資料庫中的所有物件。  
  
-   授與了非預設的權限。  
  
 您可以利用下列方式來更正這些狀況：  
  
-   使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工具和程式，然後再次執行 **sp_certify_removable** 。  
  
-   您只需使用**auto**值來執行**sp_certify_removable** 。  
  
 請注意，這個預存程序只會檢查使用者和使用者權限。 您可以將群組加入資料庫中，以及將權限授與這些群組。 如需詳細資訊，請參閱 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)的相關資訊。  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色的成員，才可執行許可權。  
  
## <a name="examples"></a>範例  
 下列範例會證明 `inventory` 資料庫已完成移除的準備。  
  
```  
EXEC sp_certify_removable inventory, AUTO;  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料庫卸離和附加 &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_create_removable &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-create-removable-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
