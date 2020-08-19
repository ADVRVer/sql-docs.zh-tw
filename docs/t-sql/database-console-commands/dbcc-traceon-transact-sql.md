---
description: DBCC TRACEON (Transact-SQL)
title: DBCC TRACEON (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC_TRACEON_TSQL
- TRACEON
- DBCC TRACEON
- TRACEON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC TRACEON statement
- trace flags [SQL Server], enabling
ms.assetid: 93085324-ebaa-4e38-aac8-5e57b4b0d36d
author: pmasl
ms.author: umajay
ms.openlocfilehash: acba012532edba5f5a94fff5b92e5f46e8b29083
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468200"
---
# <a name="dbcc-traceon-transact-sql"></a>DBCC TRACEON (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

啟用指定的追蹤旗標。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```syntaxsql
DBCC TRACEON ( trace# [ ,...n ][ , -1 ] ) [ WITH NO_INFOMSGS ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>引數
*trace#*  
這是您要開啟的追蹤旗標編號。  
  
*n*  
這是一個預留位置，表示可以指定多個追蹤旗標。  
  
-1  
在指定的追蹤旗標上進行全域切換。 Azure SQL 受控執行個體中需要這個引數。 
  
WITH NO_INFOMSGS  
隱藏所有參考訊息。  
  
## <a name="remarks"></a>備註  
在實際伺服器上，為了防止無法預期的行為發生，我們建議您使用下列一種方法，僅在伺服器範圍啟用追蹤旗標：
-   使用 Sqlservr.exe 的 **-T** 命令列啟動選項。 這是建議採用的最佳做法，因為它可以確定所有的陳述式在執行時，都啟用追蹤旗標。 其中包括啟動指令碼中的命令。 如需詳細資訊，請參閱 [sqlservr Application](../../tools/sqlservr-application.md)。  
-   只有當使用者或應用程式未在系統上並行執行陳述式時，才使用 DBCC TRACEON **(** _trace#_ [ **,** ... *.n*] **,-1)** 。  

追蹤旗標用來控制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的運作方式來自訂特定性質。 追蹤旗標在啟用之後，會在伺服器中保持啟用狀態，直到您執行 DBCC TRACEOFF 陳述式停用它為止。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中有兩種類型的追蹤旗標：工作階段和全域。 工作階段追蹤旗標用於某個連接，而且只會在該連接顯示出來。 全域追蹤旗標是設在伺服器層級，只要是該伺服器上的連接，都看得到它們。 若要判定追蹤旗標的狀態，請使用 DBCC TRACESTATUS。 若要停用追蹤旗標，請使用 DBCC TRACEOFF。
  
在開啟影響查詢計劃的追蹤旗標之後，執行 `DBCC FREEPROCCACHE;` 以使用影響計畫的新行為重新編譯快取的計劃。

Azure SQL 受控執行個體支援下列全域追蹤旗標：460、2301、2389、2390、2453、2467、7471、8207、9389、10316 與 11024

## <a name="result-sets"></a>結果集  
 DBCC TRACEON 會傳回下列結果集 (訊息)：  
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>權限  
需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。
  
## <a name="examples"></a>範例  
下列範例會在追蹤旗標 `3205` 上進行切換，來停用磁帶驅動程式的硬體壓縮。 這個旗標只會在目前連接進行切換。
  
```sql  
DBCC TRACEON (3205);  
GO  
```  
  
下列範例會在追蹤旗標 `3205` 上進行全域切換。
  
```sql  
DBCC TRACEON (3205, -1);  
GO  
```  
  
下列範例會在追蹤旗標 `3205` 和 `260` 上進行全域切換。
  
```sql  
DBCC TRACEON (3205, 260, -1);  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC TRACEOFF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceoff-transact-sql.md)  
[DBCC TRACESTATUS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-tracestatus-transact-sql.md)  
[追蹤旗標 &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
[啟用影響計劃的 SQL Server 查詢最佳化工具行為，此行為在特定查詢層級可以不同的追蹤旗標控制](https://support.microsoft.com/kb/2801413) \(機器翻譯\)
  
  
