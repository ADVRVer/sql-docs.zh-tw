---
title: DBCC FLUSHAUTHCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 00497dfe67c03eab4d9d0bc1798f6d5537628ed7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "68101946"
---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

針對[!INCLUDE[ssSDS](../../includes/sssds-md.md)]中目前的使用者資料庫，清空包含登入和防火牆規則相關資訊的資料庫驗證快取。 此陳述式不適用於邏輯 master 資料庫，因為 master 資料庫包含登入和防火牆規則相關資訊的實體儲存體。 執行陳述式的使用者和目前連線的其他使用者會保持連線。 ([!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] 目前不支援 DBCC FLUSHAUTHCACHE。)
 
![文章連結圖示](../../database-engine/configure-windows/media/topic-link.gif "文章連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>引數  
無。
  
## <a name="remarks"></a>備註  
驗證快取會複製儲存在 master 資料庫中的登入與伺服器防火牆規則，然後放在使用者資料庫的記憶體中。  因為自主資料庫使用者的資訊已儲存在使用者資料庫中，所以自主資料庫使用者不是驗證快取的一部分。
持續作用中的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 連線至少每 10 小時就需要授權 (由[!INCLUDE[ssDE](../../includes/ssde-md.md)]執行)。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]會嘗試使用最初提交的密碼重新授權，而且不需要使用者輸入。 基於效能考量，當密碼在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 中重設時，不會重新驗證連線，即使連線因為連線共用而重設。 這和內部部署 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的行為不同。 如果自從連線初始授權後密碼已經變更，則必須中斷該連線，然後使用新密碼建立新連線。 具有 KILL DATABASE CONNECTION 權限的使用者可以使用 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]KILL &#40;Transact-SQL&#41;[ 命令明確地中斷對 ](../../t-sql/language-elements/kill-transact-sql.md) 的連線。
  
## <a name="permissions"></a>權限  
需要 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 系統管理員帳戶。
  
## <a name="example"></a>範例  
下列陳述式會清除目前資料庫的驗證快取。
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>另請參閱  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
