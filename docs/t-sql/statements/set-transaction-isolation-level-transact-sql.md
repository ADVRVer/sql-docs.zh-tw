---
title: SET TRANSACTION ISOLATION LEVEL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LEVEL
- LEVEL_TSQL
- SET TRANSACTION ISOLATION LEVEL
- ISOLATION
- ISOLATION_TSQL
- SET_TRANSACTION_ISOLATION_LEVEL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET TRANSACTION ISOLATION LEVEL statement
- row versioning [SQL Server], isolation levels
- TRANSACTION ISOLATION LEVEL option
- isolation levels [SQL Server], setting
- locking [SQL Server], isolation levels
- transactions [SQL Server], isolation levels
ms.assetid: 016fb05e-a702-484b-bd2a-a6eabd0d76fd
caps.latest.revision: 80
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: bdc4fa9efaa2637df367231d5dc6e58fe0703e9c
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39456782"
---
# <a name="set-transaction-isolation-level-transact-sql"></a>SET TRANSACTION ISOLATION LEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  控制 [!INCLUDE[tsql](../../includes/tsql-md.md)] 連接所發出之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 陳述式的鎖定和資料列版本設定行為。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>語法

```
-- Syntax for SQL Server and Azure SQL Database
  
SET TRANSACTION ISOLATION LEVEL
    { READ UNCOMMITTED
    | READ COMMITTED
    | REPEATABLE READ
    | SNAPSHOT
    | SERIALIZABLE
    }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse
  
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED
```

## <a name="arguments"></a>引數  
 READ UNCOMMITTED  
 指定陳述式可以讀取其他交易已修改，但尚未認可的資料列。  
  
 在 READ UNCOMMITTED 層級執行的交易不會發出共用鎖定來防止其他交易修改目前交易所讀取的資料。 防止目前交易讀取其他交易已修改而尚未認可之資料列的獨佔鎖定，也不會封鎖 READ UNCOMMITTED 交易。 當設定這個選項時，可能會讀取到尚未認可的修改項目，這稱為中途讀取 (Dirty Read)。 在交易結束之前，資料中的值可以變更，資料列也可以在資料集中出現或消失。 這個選項的效果，與在交易中將所有 SELECT 陳述式之所有資料表設為 NOLOCK 相同。 這是隔離等級中限制最少的一種。  
  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，您也可以利用下列兩個等級之一，防止交易讀到尚未認可的資料修改 (中途讀取)，同時將鎖定競爭的情況降到最低：  
  
-   READ_COMMITTED_SNAPSHOT 資料庫選項設為 ON 的 READ COMMITTED 隔離等級。  
  
-   SNAPSHOT 隔離等級。  
  
 READ COMMITTED  
 指定陳述式不能讀取其他交易已修改而尚未認可的資料。 這個選項可避免中途讀取。 目前交易內個別陳述式之間的其他交易可以變更資料，這會產生不可重複的讀取或虛設項目資料。 這個選項是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設值。  
  
 READ COMMITTED 的行為會隨著 READ_COMMITTED_SNAPSHOT 資料庫選項的設定而不同：  
  
-   如果 READ_COMMITTED_SNAPSHOT 設為 OFF (預設值)，當目前交易正在執行讀取作業時，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會利用共用鎖定來防止其他交易修改資料列。 共用鎖定也會封鎖陳述式，使它們在其他交易完成之前，無法讀取其他交易所修改的資料列。 共用鎖定類型會決定釋放的時機。 資料列鎖定會在處理下一個資料列之前釋放。 頁面鎖定會在讀取下一個頁面時釋放，而資料表鎖定會在陳述式完成時釋放。  
  
    > [!NOTE]  
    >  如果 READ_COMMITTED_SNAPSHOT 設為 ON，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會利用資料列版本設定，依照資料在陳述式開始時就存在的狀態，向每個陳述式提供具有交易一致性的資料快照集。 鎖定的使用目的不是為了防止其他交易更新資料。  
    >   
    >  快照集隔離支援 FILESTREAM 資料。 在快照集隔離模式下，交易中的任何陳述式所讀取之 FILESTREAM 資料，都會是交易啟動時就存在之資料的交易一致性版本。  
  
 當 READ_COMMITTED_SNAPSHOT 資料庫選項是 ON 時，您可以利用 READCOMMITTEDLOCK 資料表提示來要求共用鎖定，而不用在執行 READ COMMITTED 隔離等級之交易的個別陳述式中設定資料列版本。  
  
> [!NOTE]  
>  設定 READ_COMMITTED_SNAPSHOT 選項時，資料庫中只允許使用執行 ALTER DATABASE 命令的連接。 在 ALTER DATABASE 完成以前，資料庫中不可以有其他開啟的連接。 資料庫不一定要處於單一使用者模式。  
  
 REPEATABLE READ  
 指定陳述式不能讀取其他交易已修改而尚未認可的資料，且在目前交易完成之前，任何其他交易都不能修改目前交易已讀取的資料。  
  
 交易中每個陳述式所讀取的所有資料都會設定共用鎖定，直到交易完成為止。 這可以防止其他交易修改目前交易已讀取的任何資料列。 其他交易仍可以插入新資料列，但必須符合目前交易所發出的陳述式搜尋條件。 如果目前交易稍後重試陳述式，便會擷取新的資料列，因而產生虛設項目讀取 (Phantom Read)。 由於共用鎖定會保留至交易完成，而不是在每個陳述式結束時釋出，因此並行發生的可能性會低於預設的 READ COMMITTED 隔離等級。 請只在必要時，才使用這個選項。  
  
 SNAPSHOT  
 指定交易中任何陳述式所讀取的資料，都是交易開始時就存在之資料的交易一致性版本。 交易只能辨識交易開始之前所認可的資料修改。 在目前交易中執行的陳述式，看不到其他交易在目前交易開始之後所進行的資料修改。 結果是交易中的陳述式會取得已認可之資料的快照集，如同資料在交易啟動時的狀態。  
  
 除非在復原資料庫，否則，SNAPSHOT 交易不會在讀取資料時要求鎖定。 讀取資料的 SNAPSHOT 交易不會封鎖其他交易寫入資料。 寫入資料的交易也不會封鎖 SNAPSHOT 交易讀取資料。  
  
 在資料庫復原的回復階段中，如果嘗試讀取另一個正在回復的交易所鎖定的資料，SNAPSHOT 交易將會要求鎖定。 SNAPSHOT 交易會被封鎖到這項交易回復為止。 獲得授權之後，會立即釋放鎖定。  
  
 ALLOW_SNAPSHOT_ISOLATION 資料庫選項必須先設為 ON，您才能啟動使用 SNAPSHOT 隔離等級的交易。 如果使用 SNAPSHOT 隔離等級的交易存取多個資料庫中的資料，每個資料庫中的 ALLOW_SNAPSHOT_ISOLATION 都必須設為 ON。  
  
 利用其他隔離等級啟動的交易不能設為 SNAPSHOT 隔離等級，否則交易將會中止。 如果是以 SNAPSHOT 隔離等級來啟動交易，您可以將它改成另一個隔離等級，再改回 SNAPSHOT。 交易會在第一次存取資料時啟動。  
  
 在 SNAPSHOT 隔離等級之下執行的交易可以檢視這項交易所進行的變更。 例如，如果交易在資料表上執行 UPDATE 之後，又發出這份資料表的 SELECT 陳述式，修改過的資料將會包含在結果集中。  
  
> [!NOTE]  
>  在快照集隔離模式下，交易中任何陳述式所讀取的 FILESTREAM 資料，都會是交易開始時 (非陳述式開頭) 就存在之資料的交易一致性版本。  
  
 SERIALIZABLE  
 指定下列項目：  
  
-   陳述式無法讀取其他交易已修改但尚未認可的資料。  
  
-   在目前交易完成之前，其他交易不能修改目前交易已讀取的資料。  
  
-   在目前交易完成之前，其他交易所插入的新資料列，其索引鍵值不能在目前交易的任何陳述式所讀取的索引鍵範圍中。  
  
 範圍鎖定會放在符合交易所執行的每個陳述式之搜尋條件的索引鍵值範圍中。 這會封鎖其他交易，以免它們更新或插入符合目前交易執行之任何陳述式的所有資料列。 這表示第二次執行交易中的任何陳述式時，它們會讀取同一組資料列。 範圍鎖定會一直保留到交易完成。 這是隔離等級最嚴格的限制，因為它鎖定了索引鍵的整個範圍，且會將鎖定保留到交易完成。 由於並行發生的可能性較低，因此，請只在必要時，才使用這個選項。 這個選項的效果，與在交易中將所有 SELECT 陳述式之所有資料表設為 HOLDLOCK 相同。  
  
## <a name="remarks"></a>Remarks  
 每次只能設定一個隔離等級選項，除非您明確變更，否則，這項設定對該連接持續有效。 除非陳述式 FROM 子句中的資料表提示為資料表指定了不同的鎖定或版本控制行為，否則，在交易內執行的所有讀取作業，都會遵照指定隔離等級的規則來運作。  
  
 交易隔離等級會定義讀取作業上取得的鎖定類型。 雖然利用讀取來參考頁面或資料表中的大量資料列時，資料列鎖定可以提升為頁面或資料表鎖定，但為了 READ COMMITTED 或 REPEATABLE READ 而取得的共用鎖定通常仍是資料列鎖定。 如果資料列被讀取之後，交易才修改資料列，交易會取得獨佔鎖定來保護這個資料列，且會保留獨佔鎖定直到交易完成為止。 例如，如果 REPEATABLE READ 交易有資料列的共用鎖定，之後交易又修改這個資料列，共用的資料列鎖定便會轉換成獨佔資料列鎖定。  
  
 但是有一個例外：您可以在交易期間隨時切換隔離等級。 從任何隔離等級變更為 SNAPSHOT 隔離時就會發生這種例外狀況。 這樣做將導致交易失敗並回復。 不過，您可以將以 SNAPSHOT 隔離等級啟動的交易變更為其他任何隔離等級。  
  
 當您變更交易的隔離等級時，會根據新等級的規則來保護變更後讀取的資源。 變更前讀取的資源則會繼續根據前一等級的規則來受到保護。 例如，如果交易從 READ COMMITTED 改成 SERIALIZABLE，變更後取得的共用鎖定現在將會保留至交易結束為止。  
  
 如果您在預存程序或觸發程序中發出 SET TRANSACTION ISOLATION LEVEL，則當物件傳回控制權時，隔離等級會重設成叫用物件時的作用等級。 例如，若您在批次中設定 REPEATABLE READ，而批次接著呼叫將隔離等級設為 SERIALIZABLE 的預存程序，則當預存程序將控制權傳回給批次時，隔離等級設定會還原為 REPEATABLE READ。  
  
> [!NOTE]  
>  使用者定義函數和 Common Language Runtime (CLR) 使用者定義類型不能執行 SET TRANSACTION ISOLATION LEVEL。 不過，您也可以使用資料表提示來覆寫隔離等級。 如需詳細資訊，請參閱[資料表提示 &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)。  
  
 當您利用 sp_bindsession 來繫結兩個工作階段時，每個工作階段都會保留它的隔離等級設定。 利用 SET TRANSACTION ISOLATION LEVEL 來變更某個工作階段的隔離等級設定，並不會影響與它繫結的任何其他工作階段的設定。  
  
 SET TRANSACTION ISOLATION LEVEL 是在執行或執行時期生效，而不是在剖析時期生效。  
  
 堆積上的最佳化大量載入作業會封鎖在下列隔離等級之下執行的查詢：  
  
-   SNAPSHOT  
  
-   READ UNCOMMITTED  
  
-   使用資料列版本設定的 READ COMMITTED  
  
 相反地，在這些隔離等級之下執行的查詢也會封鎖堆積上的最佳化大量載入作業。 如需大量匯入作業的詳細資訊，請參閱[資料的大量匯入及匯出 &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)。  
  
 具 FILESTREAM 功能的資料庫支援下列交易隔離等級。  
  
|隔離等級|Transact SQL 存取|檔案系統存取|  
|---------------------|-------------------------|------------------------|  
|讀取未認可|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|不支援|  
|讀取認可|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|可重複讀取|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|不支援|  
|可序列化|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|不支援|  
|讀取認可的快照集|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|快照式|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
## <a name="examples"></a>範例  
 下列範例會設定工作階段的 `TRANSACTION ISOLATION LEVEL`。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會保留後來每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 陳述式的所有共用鎖定，直到交易完成為止。  
  
```  
USE AdventureWorks2012;  
GO  
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;  
GO  
BEGIN TRANSACTION;  
GO  
SELECT *   
    FROM HumanResources.EmployeePayHistory;  
GO  
SELECT *   
    FROM HumanResources.Department;  
GO  
COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [DBCC USEROPTIONS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-useroptions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET 陳述式 &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [資料表提示 &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
